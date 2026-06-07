---
exo__Asset_uid: 6057ffea-dcac-4feb-846e-b9d4f35fddb8
exo__Asset_isDefinedBy: "[[2ce77ac1-3f78-4f64-9dc1-41ea01da1ef0]]"
exo__Asset_createdAt: 2026-05-16T20:05:44
exo__Asset_updatedAt: 2026-05-16T20:05:44
exo__Asset_createdBy: "[[de20a3f1-7483-4714-ab28-b45f5cf02c76]]"
exo__Instance_class:
  - "[[5398b88a-3324-4fb4-91d2-d66359b5f720]]"
exo__Asset_label: Bash standalone grep/find/cat blocked — wrap in pipe or use dedicated tool
aliases:
  - feedback bash standalone tool block
exo__Asset_description: PreToolUse hook bash-prefer-dedicated.sh blocks standalone grep/find/cat/awk/sed invocations. Wrap в pipe/heredoc или используй Grep/Glob/Read/Edit dedicated tools.
inbox__ExoAssistantKnowledge_decay: "[[40578231-ab64-4f8a-8192-db4c55022125]]"
inbox__ExoAssistantKnowledge_confidence: "[[227def30-f56f-4f5f-936d-f6a81ad73c96]]"
inbox__ExoAssistantKnowledge_lastReinforcedAt: 2026-05-16T20:05:44
---

## Правило

Hook `~/.claude/hooks/bash-prefer-dedicated.sh` блокирует standalone вызовы `grep`, `find`, `cat`, `head`, `tail`, `awk`, `sed` в Bash tool. Если нужен shell context — обернуть в pipe / heredoc / multi-step composition.

### Decision tree

| Use case | Allowed |
|---|---|
| Single search `grep PATTERN file.md` | ❌ → use `Grep` tool |
| Single read `cat file.md` | ❌ → use `Read` tool |
| Single find `find . -name X.md` | ❌ → use `Glob` tool |
| Sed in-place edit `sed -i '' 's/A/B/' file` | ❌ → use `Edit` tool |
| `grep ... \| xargs ...` (piped composition) | ✅ allowed |
| `find ... -print0 \| xargs -0 ...` | ✅ allowed |
| `cat << EOF \| python3 ...` (heredoc) | ✅ allowed |
| Multi-step `find ... \| head -1 \| while read f; do ...; done` | ✅ allowed |

## Why

- Dedicated tools faster (token-economical), more deterministic results
- 1083+ violations / 7 days observed empirically (telemetry from hook block messages)
- Standalone commands иногда возвращают cached/wrong data на macOS BSD vs GNU coreutils

## How to apply

- Reflex: "хочу запустить bash" → подумать «есть ли dedicated tool?»
- Если есть pipe/composition — bash OK
- Если single-op — переключиться на dedicated tool с первой попытки

## Прецедент

Session 2026-05-16 SHACL deep-dive — 5+ hook blocks за одну сессию (standalone find, grep, cat, awk). Каждый block тратит token budget на retry + cognitive overhead. Habit формируется только через явное правило в aiKnow.
