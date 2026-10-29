---
exo__Asset_uid: c5be4eab-cbd8-4dd0-b69a-47cd53b0a386
exo__Asset_createdAt: 2026-09-14T11:08:03
exo__Asset_updatedAt: 2026-10-29T14:03:51
exo__Instance_class:
  - "[[dda12c48-6886-4624-8710-ed4ba92ce2b3]]"
exo__Asset_createdBy: "[[4ef3962d-b8a7-42b5-bd28-88ec846f1d13]]"
exo__Asset_label: "mark-done отказывает: нет startTimestamp"
aliases:
  - "mark-done отказывает: нет startTimestamp"
  - mark-done refused no startTimestamp
  - start-effort провалился тихо
  - нельзя закрыть эффорт без старта
  - effort has no startTimestamp
exo__Asset_isDefinedBy: "[[2ce77ac1-3f78-4f64-9dc1-41ea01da1ef0]]"
---

Симптом: при закрытии узла хук/команда `mark-done` отказывает «нет `startTimestamp`», хотя исполнитель отчитался, что взял работу — его `apply start-effort` провалился тихо (precondition, не тот статус, другой vault). Чинится восстановлением старта, а не обходом гейта.

