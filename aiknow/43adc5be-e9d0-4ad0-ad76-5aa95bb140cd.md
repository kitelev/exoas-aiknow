---
exo__Asset_uid: 43adc5be-e9d0-4ad0-ad76-5aa95bb140cd
exo__Asset_createdAt: 2026-09-21T10:19:03
exo__Asset_updatedAt: 2026-09-21T23:19:15
exo__Instance_class:
  - "[[39a39239-2a97-483a-ba91-fb01bf5c85f3]]"
exo__Asset_createdBy: "[[4ef3962d-b8a7-42b5-bd28-88ec846f1d13]]"
exo__Asset_label: "Правило: artifact-class-neighbour-check (полный текст; пилот rules-from-graph, 2026-09-06)"
aliases:
  - "Правило: artifact-class-neighbour-check (полный текст; пилот rules-from-graph, 2026-09-06)"
  - artifact-class-neighbour-check
exo__Asset_isDefinedBy: "[[2ce77ac1-3f78-4f64-9dc1-41ea01da1ef0]]"
inbox__ExoAssistantKnowledge_decay: "[[06a5b9f9-da93-4234-883f-3f0cf65b2fba]]"
inbox__ExoAssistantKnowledge_confidence: "[[227def30-f56f-4f5f-936d-f6a81ad73c96]]"
---
<!-- Added by /session-retrospective 2026-05-30 — root: premature /rfc invocation для plugin bug fix; pivoted mid-flow к ems__Task pattern -->

# Artifact class selection: neighbour-pattern check перед heavy ceremony

⛤ **Шире имени файла (замер 2026-09-02, фальсификатор №5): 4 строки индекса из 6 — НЕ про выбор класса.**
Общий предмет шести разборов — **«прежде чем СОЗДАТЬ, посмотри, что уже есть, и чем оно от твоего
отличается»**: класс артефакта (тело ниже) · анкер и аудитория (§A1, §A2) · дедуп концептов (§A4) ·
дедуп тикетов (§A5) · дедуп значений в словаре (§A6). ⚠ Пришедший с вопросом «как не завести дубль
тикета» по имени файла сюда **не пойдёт** — заходить по индексу.

<!-- Added by /session-retrospective 2026-09-05 (vteam-115a66f6, MemberArchitect) — root: спека предписала форму пути в spec.json по памяти; замер соседей дал обратное (50/51). -->
⛤ **И шире VAULT: тот же floor у КОНФИГА-СПУТНИКА** (`<stem>.spec.json`, `*.plist`, `*.config.*`
рядом с кодом). Форму его полей — путь, ключ, значение — брать **замером соседей**
(`python3 -c` по каталогу, посчитать доминирующую форму), а не по памяти. ⚠ **Tell:** ты пишешь
поле нового конфига, глядя на СВОЙ прототип (фикстуру, черновик), а не на живых соседей.
⛔ Обе формы могут **работать** (симлинк, раскрытие `$HOME`) — тогда это вопрос конвенции, и
«работает» её не заменяет: расхождение читается следующим автором как новый паттерн.
_(2026-09-05, тикет `115a66f6`: спека предписала `harness: bash $HOME/.claude/bin/…`; замер
51 живого spec — **50** пишут `$HOME/dotfiles/.claude/bin/…`. Поймано ретро, не реализацией.)_

<!-- Added by /session-retrospective 2026-09-09 (vteam-115a66f6, MemberTester) — root: floor выше исполнен, а вывод по одному полю перенесён на соседнее; замер того же корпуса дал ОБРАТНУЮ конвенцию. -->
⛔ **Замеряется КАЖДОЕ поле отдельно: у полей ОДНОГО файла конвенции бывают ПРОТИВОПОЛОЖНЫЕ,
и перенос вывода с поля на поле — тот же промах «по памяти», только с цифрой в руках.**
Floor выше при этом исполнен (замер был), поэтому tell про «свой прототип» молчит.
⚠ **Tell:** во фразе есть «тоже» / «аналогично» / «для такого предмета большинство» — то есть
ты распространяешь посчитанное на НЕпосчитанное. ✅ Печатать `Counter` по КАЖДОМУ полю,
которое пишешь, и сверять со своим значением поимённо.
_(2026-09-09, тот же тикет, приёмка: замер 59 spec — `harness` **58/59** dotfiles-форма,
а `subject` **41/59** `$HOME/.claude` — доминанты РАЗНЫЕ. Спека предсказала для `subject`
dotfiles «как у большинства»; реализация написала по факту и оказалась права.)_

⛔ **Замер доминанты отвечает «как ПРИНЯТО», но НЕ отвечает «обязательно ли» — и чинить
недоминантную форму бывает дороже, чем оставить.** Инструмент, которым ты создаёшь ассет
(`create`), пишет поле в форме, отличной от доминанты корпуса; floor выше («сверить со своим
значением поимённо») читается тогда как «привести к доминанте», и рука тянется дописать разницу
Edit'ом — по **guarded**-полю, мимо CLI.

- ✅ **Второй вопрос закрывается ИСПОЛНЕНИЕМ, а не пересчётом:** предъяви, что недоминантная
  форма даёт нужный ТРИПЛ — SPARQL по живому соседу, который её уже несёт. Даёт ⇒ форма рабочая,
  оставить как пишет инструмент, и сказать это вслух в отчёте.
- ⚠ **Tell:** доминанта посчитана, твоё значение от неё отличается, а разницу создал НЕ ты, а
  инструмент.

_(2026-09-10, `8c2cddf7`: `exo__Class_superClass` — список **61** : скаляр **2**, `create` пишет
скаляр; SPARQL на живом `exo__DependencyKind` (скаляр) вернул трипл ⇒ не чинил, и созданный класс
штатно попал в выборку потомков `exo__Enum`.)_

Перед offer'ом / invocation'ом heavy-ceremony skill (`/rfc`, `/onto-rfc`, `/pmbok-init`, etc.) для нового vault asset — **обязательная mechanical pre-check**: посмотреть на ~3 свежих соседей в target inbox/ и определить, какой класс реально применяется для analogous work.

## Когда правило срабатывает

- Пользователь описал работу размера 1 PR / 1 фича / 1 баг fix.
- Cobrazn artifact для tracking work (vault asset class) ещё не выбран.
- Estimating whether ems__Task / inbox__ExoAssistantKnowledge (RFC) / pmbok__ProjectCharter / pmbok__IssueItem / другое.

## Mechanical pre-check (≤30 seconds)

```bash
# 1. Свежие соседи в target inbox/ (⛔ пути ИСПРАВЛЕНЫ 2026-09-02 — прежние были МЕРТВЫ, замер:
#    корневого vault-exodev/inbox/ не существует, а vault-2025 декоммиссирован 2026-06-27
#    вместе с деревом 03 Knowledge/. Копируемый блок вёл в никуда.)
ls -lt ~/vaults/vault-exodev/assetspaces/kitelev/exoas-exodev/inbox/*.md 2>/dev/null | head -5

# 2. Прочитать верхний — ФОРМУ exo__Instance_class
#    (⛔ standalone `head`/`cat` блокирует bash-prefer-dedicated: либо Read-тулом, либо через пайп)
grep -m1 -A3 'exo__Instance_class' <newest-uuid>.md | cat

# 3. Match against ontology:
#    1b20a8f0-... = ems__Task (lightweight, execution-level)
#    b0474610-... = inbox__ExoAssistantKnowledge (RFC, formal review-cycle)
#    985f6c53-... = pmbok__ProjectCharter (project initiation)
#    7db5eeff-... = ems__Project (multi-task tracking)
```

⚠ **`ls -lt … | head -5` отвечает на вопрос о КЛАССЕ и НЕ годится для АНКЕРА:** §A1 требует перечислить
**ВСЕ** инстансы с их `isDefinedBy` (конвенция бывает расщеплена, и одного соседа мало). Топ-5 по времени —
выборка, а не перечисление; для анкера — SPARQL по всем инстансам класса.

## Decision matrix

| Neighbour pattern | Work shape this session | Use this class |
|---|---|---|
| ems__Task siblings ("Plugin fix: …", "Followup: …") | Single PR plugin bug fix / refactor | `ems__Task` (1b20a8f0) |
| Mix of ems__Task + occasional inbox__ExoAssistantKnowledge RFC | Default to ems__Task; reserve RFC for new architectural decisions | `ems__Task` unless RFC explicitly justified |
| Only inbox__ExoAssistantKnowledge RFCs | Truly RFC-track inbox | `inbox__ExoAssistantKnowledge` |
| pmbok__ProjectCharter / pmbok__Project — only if user explicitly invoking PMBOK lifecycle | Multi-phase formal project | PMBOK classes |

## Anti-pattern

⛔ Offer'ить «оформить как RFC + Issue» прежде чем посмотреть neighbours. Если соседние ассеты — ems__Task, default к ems__Task. RFC ceremony расходует ~50% extra context tokens (Phase 0 empirical spike → Phase 2 scope picker → Phase 3 delegation → Phase 3b status augmentation → Phase 5 critical review) и **редко** добавляет value для single-PR work, где review происходит на GitHub Issue / PR layer.

⛔ Считать «RFC + Issue» дефолтным offer'ом. RFC должен быть offered только когда:
- Work cross-cutting (≥2 PRs планируются)
- Architectural decision с trade-offs нуждается в documented rationale
- Formal review-cycle нужен до execution
- Onto-changes (новый класс, изменения domain/range, facets)

В остальных случаях — `ems__Task` + GitHub Issue достаточно.

## ⛔ Dedup обязан назвать КЛАСС найденного — «похожее» часто оказывается НЕ тем классом

Совпадение по `exo__Asset_label` не различает `ems__Task`, `ems__TaskPrototype` и `ems__Reminder`:
у прототипа **нет статуса по построению**, его нельзя запланировать и на него нельзя повесить
напоминание. Показ «название + статус» у прототипа печатает пустоту и выдаёт шаблон за задачу.

- ⚠ **Tell, ловится ЧТЕНИЕМ своего же запроса:** он тянет `SELECT ?s ?l` — класса в ответе нет
  ВООБЩЕ, значит назвать его нечем, даже если захочешь.
- ✅ **Floor:** `OPTIONAL { ?s exo:Instance_class ?c }` в dedup-запросе + класс в тексте ответа.
- ⛔ Прототип — не «существующая задача»: из него делают экземпляр (`apply create-task-instance`),
  и планируют уже его.

_(2026-09-07: T-Bank-бот назвал `ems__TaskPrototype` «похожей задачей» и предложил её планировать;
по одной метке в графе лежали ТРИ ассета РАЗНЫХ классов — Task, TaskPrototype, Reminder.)_

## Разборы случаев — ВЫНЕСЕНЫ В ГРАФ (справочник on-demand)

⛤ **6 разборов** (~32 КБ) — справочник on-demand: читают, когда механизм **уже соврал**, а не перед действием.

| # | дата | Тема (симптом ⇒ действие) |
|---|---|---|
| **§A1** | `2026-07-24` | Копируешь `exo__Asset_isDefinedBy` у ОДНОГО соседа того же класса ⇒ конвенция класса бывает РАСЩЕПЛЕНА, и копия наследует чужой выбор АУДИТОРИИ ⇒ перечислить ВСЕ инстансы с анкерами одним SPARQL; единообразно ⇒ копировать можно, расщеплено ⇒ выбирать по СЕМАНТИКЕ контента. ⛔ Неверный анкер = утечка приватности ⇒ §A1 |
| **§A2** | `2026-08-02` | Создаёшь НОВУЮ онтологию и привязываешь к её анкеру ВСЁ, включая экземпляры ⇒ co-location кладёт ассет в папку его онтологии, а у ассетспейса есть АУДИТОРИЯ ⇒ анкеры РАЗНЫЕ: TBox → `exoas-public`, ABox → пространство аудитории данных. ⚠ Tell — `ls`, куда ФАКТИЧЕСКИ легли экземпляры ⇒ §A2 |
| **§A3** | `2026-08-12` | copy-from-neighbour у ЗРЕЛОГО ассета ⇒ вместе со свойствами копируется ПРОЗА ТЕЛА с утверждениями о поведении движка, которые стареют вместе с кодом ⇒ N копий = N носителей одного ложного утверждения ⇒ техническое утверждение эталона проверять `git grep` по `origin/main` ПЕРЕД копированием ⇒ §A3 |
| **§A4** | `2026-08-16` | Dedup по русскому слову вернул НОЛЬ общих понятий — только частные случаи ⇒ каноническое имя концепта тут часто АНГЛИЙСКОЕ, а русское живёт в `exo__Asset_aliases` ⇒ один запрос ОБОИМИ языками И по алиасам, по КОРНЮ слова. ⛔ Цена промаха — дубль поверх ЦЕНТРА таксономии ⇒ §A4 |
| **§A5** | `2026-08-24` | Заводишь тикет «смежная находка → отдельный тикет» ⇒ у ОБЩЕГО инструмента ты почти никогда не первый: дефект бьёт по КАЖДОМУ исполнителю, дубли растут линейно ⇒ запрос по work-item'ам ДО `create` (фильтр по `ems__Effort_status` обязателен) + свип по дизъюнкции 2-3 ключей РАЗНЫХ слоёв ⇒ §A5 |
| **§A6** | `2026-08-26` | Выделяешь имя из КОНЕЧНОГО множества общего скрипта (код возврата, маркер, env) и читаешь занятое из файла ⇒ файл показывает ПРОШЛОЕ, а множество делят тикеты В ПОЛЁТЕ ⇒ перечислить тикеты доски по ТОМУ ЖЕ файлу и прочитать их §Что сделать (форма запроса — §A5) ⇒ §A6 |

⛤ **Справочник:** `072bb8ff-9411-4db7-83c1-19c561a449ca`, якоря **§A1-§A6**.
Рецепт адресного чтения (один на корпус) — `rule-carrier-follows-function` §«Читать справочник АДРЕСНО».


## Cross-references

- `~/dotfiles/.claude/rules/vault-asset-creation.md` — adjacent rule covers PATH selection (vault-2025 vs vault-exodev, exception list); этот rule covers CLASS selection (`ems__Task` vs `inbox__ExoAssistantKnowledge` vs PMBOK) + (Addendum) isDefinedBy/audience-anchor selection.
- `~/dotfiles/.claude/rules/dogfood-vault-search-sparql-first.md` — ⛔ **ЧЕМ** делать запрос, который предписывают §A1 · §A4 · §A5 · §A6: SPARQL, а НЕ `grep -r` (рекурсивный греп каноничного vault блокирует хук).
- `~/dotfiles/.claude/rules/multi-agent-review-vs-user-validation.md` — sibling rule on validating user intent through interview before heavy onto-RFC execution; этот rule applies earlier (artifact-class selection, before any skill invocation).
- `~/dotfiles/.claude/rules/rfc-first-verification.md` — sibling rule about reading RFC source artifacts before re-interviewing user; complementary direction (don't duplicate; consult source).

⛤ **Эмпирика** (3 фрагм.: 2 секц. + 1 абз.) → `~/.claude/rules-archive/artifact-class-neighbour-check.md`

