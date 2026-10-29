---
exo__Asset_uid: 65a8dcb3-7fe3-4420-bef3-ba1edaad8c6d
exo__Asset_createdAt: 2026-09-14T12:23:18
exo__Asset_updatedAt: 2026-10-29T13:41:33
exo__Instance_class:
  - "[[dda12c48-6886-4624-8710-ed4ba92ce2b3]]"
exo__Asset_createdBy: "[[4ef3962d-b8a7-42b5-bd28-88ec846f1d13]]"
exo__Asset_label: gh issue --search вернул чужие репо
aliases:
  - gh issue --search вернул чужие репо
  - gh issue list --search leaks into global GitHub search
  - false dedup result from other repos
  - search OR в gh issue list
  - issue dedup нашёл чужой репозиторий
  - repo ignored with --search
exo__Asset_isDefinedBy: "[[2ce77ac1-3f78-4f64-9dc1-41ea01da1ef0]]"
---

Симптом: `gh issue list --repo X --search "A OR B"` возвращает issues из ЧУЖИХ репозиториев — `--search` уходит в глобальный поиск GitHub, и dedup-проверка «такой issue уже есть» даёт ложный результат. Сужать поиск квалификатором `repo:` внутри строки поиска.

