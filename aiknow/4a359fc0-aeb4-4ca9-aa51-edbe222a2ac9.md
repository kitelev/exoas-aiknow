---
exo__Asset_uid: 4a359fc0-aeb4-4ca9-aa51-edbe222a2ac9
exo__Asset_createdAt: 2026-09-14T11:47:20
exo__Asset_updatedAt: 2026-10-29T13:34:48
exo__Instance_class:
  - "[[dda12c48-6886-4624-8710-ed4ba92ce2b3]]"
exo__Asset_createdBy: "[[4ef3962d-b8a7-42b5-bd28-88ec846f1d13]]"
exo__Asset_label: Edit не находит строку, скопированную дословно
aliases:
  - Edit не находит строку, скопированную дословно
  - Edit cannot match a verbatim-copied string
  - String to replace not found
  - невидимый юникод-пробел
  - якорь с префиксом из своего вывода
  - anchor 0 совпадений
exo__Asset_isDefinedBy: "[[2ce77ac1-3f78-4f64-9dc1-41ea01da1ef0]]"
---

Симптом: `Edit`/`assert s.count(old)==1` не матчит строку, только что показанную `Read`/выводом, и сужение old_string не помогает. Либо в файле невидимый кодпоинт (U+202F/U+00A0), либо якорь скопирован из своего вывода с префиксом/отступом, либо файл сдвинула твоя же правка сигнатуры.

