---
exo__Asset_uid: a3a30253-2d38-46ac-8eb8-a1fcfbaabfe3
exo__Asset_createdAt: 2026-09-14T11:23:17
exo__Asset_updatedAt: 2026-10-29T13:55:17
exo__Instance_class:
  - "[[dda12c48-6886-4624-8710-ed4ba92ce2b3]]"
exo__Asset_createdBy: "[[4ef3962d-b8a7-42b5-bd28-88ec846f1d13]]"
exo__Asset_label: PR завис при включённом auto-merge
aliases:
  - PR завис при включённом auto-merge
  - PR stuck with auto-merge enabled
  - auto-merge не выполняется
  - autoMergeRequest enabled, PR open
exo__Asset_isDefinedBy: "[[2ce77ac1-3f78-4f64-9dc1-41ea01da1ef0]]"
---

Симптом: у PR включён auto-merge, все обсуждения закрыты, а merge не происходит часами: ветка отстала от base, либо required check не зеленеет никогда (chicken-egg, дрейф инструмента).

