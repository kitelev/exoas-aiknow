---
exo__Asset_uid: 2c0eeedb-b300-4fa0-b9ec-d395cec8fca4
exo__Asset_createdAt: 2026-10-03T03:29:21
exo__Asset_updatedAt: 2026-10-03T03:30:46
exo__Instance_class:
  - "[[39a39239-2a97-483a-ba91-fb01bf5c85f3]]"
exo__Asset_createdBy: "[[4ef3962d-b8a7-42b5-bd28-88ec846f1d13]]"
exo__Asset_label: "Правило: string-replace-dollar-corruption (полный текст; пилот rules-from-graph, 2026-09-06)"
aliases:
  - "Правило: string-replace-dollar-corruption (полный текст; пилот rules-from-graph, 2026-09-06)"
  - string-replace-dollar-corruption
exo__Asset_isDefinedBy: "[[2ce77ac1-3f78-4f64-9dc1-41ea01da1ef0]]"
inbox__ExoAssistantKnowledge_decay: "[[06a5b9f9-da93-4234-883f-3f0cf65b2fba]]"
inbox__ExoAssistantKnowledge_confidence: "[[227def30-f56f-4f5f-936d-f6a81ad73c96]]"
aiKnow__Memory_aboutConcept:
  - "[[16a725fd-8ef7-425a-af5b-abdec027b325]]"
  - "[[2d96edeb-3c17-4598-863c-c16476fdb97f]]"
  - "[[83d44fae-29a4-40fa-ac95-bbdf02129102]]"
---

---
paths:
  - "**/packages/**"
  - "**/.github/**"
  - "**/*.ts"
  - "**/*.tsx"
  - "**/*.js"
  - "**/*.mjs"
  - "**/*.test.ts"
  - "**/jest.config*"
---
<!-- Added by /session-retrospective 2026-07-12 — root: #3800 review M1 (repair-frontmatter built the file via content.replace(match[0], newBlock) → $$/$&/$1 in frontmatter VALUES silently corrupted). Same class as #3795 H1. -->

# `String.prototype.replace(target, replacementString)` interprets `$$` / `$&` / `` $` `` / `$'` / `$N` in the REPLACEMENT — corrupts data-bearing content

## Принцип

Второй аргумент `str.replace(target, replacement)` — когда он **строка** — НЕ вставляется дословно: JS интерпретирует `$`-паттерны в нём как special replacement patterns:

| Паттерн | Что подставляется |
|---|---|
| `$$` | литеральный `$` |
| `$&` | весь заматченный `target` |
| `` $` `` | всё ДО матча |
| `$'` | всё ПОСЛЕ матча |
| `$1`..`$99` | capture-группа N (если target — regex с группами) |

Если `replacement` строится из **данных пользователя / файла** (frontmatter-значение, заметка, имя, URL, любой контент, который может содержать `$`), эти паттерны **молча искажают** результат — особенно коварно в **repair/format/rewrite-тулах, которые обязаны сохранять контент байт-в-байт**. Значение вроде `"cost $$100 & $& ref"` превратится в `"cost $100 & <ВЕСЬ БЛОК> ref"`.

## Когда правило срабатывает

- Строишь новое содержимое файла/строки через `content.replace(block, newBlockString)` где `newBlockString` содержит пользовательские значения.
- Формат/repair/dedupe/rewrite-тул (frontmatter, YAML, JSON, markdown), которому нельзя менять значения.
- `label.replace(x, userValue)`, `template.replace(placeholder, dataFromVault)` и т.п.

## Что делать

- ✅ **Function-replacer** — `str.replace(target, () => replacement)`. Возвращаемая функцией строка вставляется **дословно**, без `$`-интерпретации. Одна строка правки.
- ✅ **Splice-by-index** (ещё надёжнее, если target `^`-anchored / индекс известен): `replacement + content.slice(match.index + match[0].length)` (или `content.slice(0, match.index) + replacement + content.slice(match.index + match[0].length)`). Ноль интерпретации + нет риска заменить ДРУГОЕ вхождение target.
- ✅ Если нужен именно string-replacement — экранируй `$` в replacement: `replacement.replace(/\$/g, "$$$$")` (перед вставкой). Менее читаемо; предпочитай function-replacer/splice.
- ⛔ Не передавай data-bearing строку как 2-й аргумент `replace` без одного из вышеперечисленных.

## Verify / тест

Тест с `$`-laden значением в данных: вход содержит `$$`, `$&`, `$1`, `` $` `` в значении + операция (dedupe/format/rewrite) → surviving значение **байт-идентично** (`toContain(dollarValue)`), ничего из regex-машинерии (`$&`→весь матч, `$1`→группа) не протекло. Revert-verify: со string-replace → RED (значение искажено), с function-replacer/splice → GREEN.
⛔ **Мутант — на КАЖДЫЙ `.replace`-сайт, фикстура — `$&`** (уточнено 2026-09-17): `$1` на паттерне БЕЗ capture-групп JS оставляет ЛИТЕРАЛОМ ⇒ ось с `$1` на таком сайте вакуумна, а `$&` разворачивает любой паттерн; один общий мутант «вернуть строки везде» не различает сайты (замер: M9d RED только после смены фикстуры `$1`→`$&`, PR #4256).

⛔ **И ВТОРАЯ ось того же гейта, которой floor выше НЕ покрывает: ПРЕДИКАТ оси, проверяющий НАЛИЧИЕ
ожидаемого фрагмента, слеп к ДУБЛИРОВАНИЮ — а именно дублирование здесь и есть порча.** Floor выше
про ФИКСТУРУ (`$&` вместо `$1`); этот — про то, ЧТО ось утверждает о результате, и он срабатывает
даже при правильной фикстуре.
- ⚠ **Механизм:** `$'` и `` $` `` не ПЕРЕНОСЯТ хвост/голову, а **КОПИРУЮТ** их в значение. Значит
  испорченный файл **по-прежнему заканчивается** ожидаемым телом — просто тело встречается в нём
  ДВА раза. Ось вида `expect(after.endsWith(SEP + BODY)).toBe(true)` на таком состоянии **истинна**,
  то есть удовлетворяется ровно тем, от чего защищает.
- ⚠ **Tell при написании оси, до прогона:** предикат сформулирован через `endsWith` / `startsWith` /
  `toContain` над величиной, которую порча **размножает**. Любой из трёх = подозрение.
- ✅ **Floor: целостность меряется КОЛИЧЕСТВОМ, а не присутствием** — «тело встречается РОВНО один
  раз» (`split(BODY).length - 1 === 1` либо счёт вхождений), и то же для разделителя `---`.
- ⛤ Дешёвый общий вид: у величины, которую операция обязана СОХРАНИТЬ, ось ассертит её **кратность**,
  а не факт наличия; тогда и перенос, и копирование различимы одним предикатом.
_(2026-10-03, #4528: ось P5 «тело байт-идентично» написана через `after.endsWith(--- + BODY)` и
ПРОШЛА под мутантом M1, возвращающим string-replacement — хвост был цел, тело скопировано в значение.
Переписана на счёт вхождений ⇒ M1 её краснит. Нашёл исполнитель, прогнав четыре предиката фолда;
чтением это не ловится, потому что предикат читается как корректный.)_

## Cross-references

- `~/.claude/skills/edit-tool-unicode-escape-becomes-codepoint/SKILL.md` — sibling «слой интерпретирует ввод не так, как ждёшь, тихо теряя/искажая данные» (там Edit `\uXXXX`→кодпоинт; тут `String.replace` `$`→special pattern).
- `~/dotfiles/.claude/rules/integration-test-revert-verify.md` — `$`-value тест как revert-verify gate.
- `~/.claude/skills/test-fixture-realism/SKILL.md` — тест на реальных data-shape значениях (с `$`), не «чистых».

⛤ **Эмпирика** (1 фрагм.) → `~/.claude/rules-archive/string-replace-dollar-corruption.md`

