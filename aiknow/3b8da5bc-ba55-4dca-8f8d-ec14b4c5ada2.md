---
exo__Asset_uid: 3b8da5bc-ba55-4dca-8f8d-ec14b4c5ada2
exo__Asset_createdAt: 2026-09-14T11:12:15
exo__Asset_updatedAt: 2026-10-29T13:27:40
exo__Instance_class:
  - "[[dda12c48-6886-4624-8710-ed4ba92ce2b3]]"
exo__Asset_createdBy: "[[4ef3962d-b8a7-42b5-bd28-88ec846f1d13]]"
exo__Asset_label: Ошибка 403 «Unable to verify organization membership»
aliases:
  - Ошибка 403 «Unable to verify organization membership»
  - 403 Unable to verify organization membership
  - 403 org membership
  - не троттл, а 403
exo__Asset_isDefinedBy: "[[2ce77ac1-3f78-4f64-9dc1-41ea01da1ef0]]"
---

Симптом: сессия падает с `403 Unable to verify organization membership`. Это не троттлинг и не 529: re-push/nudge бесполезен по построению — отказ идёт от проверки принадлежности аккаунта к организации, чинится на стороне авторизации, не повтором.

