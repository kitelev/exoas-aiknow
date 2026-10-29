---
exo__Asset_uid: 8d8cf1ed-d8b3-4207-ae9b-ab5bfab9a947
exo__Asset_createdAt: 2026-09-14T11:38:36
exo__Asset_updatedAt: 2026-10-29T13:51:47
exo__Instance_class:
  - "[[dda12c48-6886-4624-8710-ed4ba92ce2b3]]"
exo__Asset_createdBy: "[[4ef3962d-b8a7-42b5-bd28-88ec846f1d13]]"
exo__Asset_label: Смерть процесса от нехватки памяти
aliases:
  - Смерть процесса от нехватки памяти
  - Process killed by memory pressure
  - SIGKILL 137
  - Jetsam
  - exit 137
  - OS cleanup убил дерево процессов
exo__Asset_isDefinedBy: "[[2ce77ac1-3f78-4f64-9dc1-41ea01da1ef0]]"
---

Симптом: процесс или дерево (дочерняя сессия, eslint в pre-commit, оркестратор) завершились SIGKILL / exit 137 без своей ошибки — системная память под давлением. System-side отказ, ортогональный API-side.

