---
exo__Asset_uid: d5af1820-b8ba-42fe-a73c-c05e51eab6db
exo__Asset_createdAt: 2026-09-14T11:39:57
exo__Asset_updatedAt: 2026-10-29T14:09:07
exo__Instance_class:
  - "[[dda12c48-6886-4624-8710-ed4ba92ce2b3]]"
exo__Asset_createdBy: "[[4ef3962d-b8a7-42b5-bd28-88ec846f1d13]]"
exo__Asset_label: Механизм существует, но его никто не вызывает
aliases:
  - Механизм существует, но его никто не вызывает
  - method never called in production
  - dead code with green tests
  - 0 callers
  - проводка не сделана
  - никто не зовёт метод
  - invalidator not wired
  - мерить читателей не носителей
  - носителей / 0 читателей
  - 0 читателей
  - читателей не носителей
  - дешёвая метрика подменила нужную
  - 65 носителей
exo__Asset_isDefinedBy: "[[2ce77ac1-3f78-4f64-9dc1-41ea01da1ef0]]"
---

Симптом: метод/скрипт/слой знаний существует, тесты на него зелёные, докстринг говорит «SHOULD call» — а `git grep` вызовов по `origin/main` пуст: ценность доказывается обращениями, не существованием. Фикс — проводка, и это новое требование, не расширение теста.

