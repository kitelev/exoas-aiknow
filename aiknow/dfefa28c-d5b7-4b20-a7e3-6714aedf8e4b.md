---
exo__Asset_uid: dfefa28c-d5b7-4b20-a7e3-6714aedf8e4b
exo__Asset_createdAt: 2026-09-14T11:29:50
exo__Asset_updatedAt: 2026-10-29T14:13:30
exo__Instance_class:
  - "[[dda12c48-6886-4624-8710-ed4ba92ce2b3]]"
exo__Asset_createdBy: "[[4ef3962d-b8a7-42b5-bd28-88ec846f1d13]]"
exo__Asset_label: Объявление зависимости втянуло лишний контур в профиль
aliases:
  - Объявление зависимости втянуло лишний контур в профиль
  - A dependency declaration pulled an extra contour into the profile
  - dependsOn ради покрытия гейта
  - рабочий vault втянут в личный
  - у объявления два потребителя
exo__Asset_isDefinedBy: "[[2ce77ac1-3f78-4f64-9dc1-41ea01da1ef0]]"
---

Симптом: правка `dependsOn` в реестре ради покрытия/гейта втянула через `includes ∪ dependsOn*` в профиль целый чужой контур (рабочий — в личный vault, тысячи файлов). У объявления два потребителя; приёмка печатает дельту замыкания.

