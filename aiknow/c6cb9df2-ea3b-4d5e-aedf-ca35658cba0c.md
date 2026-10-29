---
exo__Asset_uid: c6cb9df2-ea3b-4d5e-aedf-ca35658cba0c
exo__Asset_createdAt: 2026-09-14T11:41:13
exo__Asset_updatedAt: 2026-10-29T14:03:53
exo__Instance_class:
  - "[[dda12c48-6886-4624-8710-ed4ba92ce2b3]]"
exo__Asset_createdBy: "[[4ef3962d-b8a7-42b5-bd28-88ec846f1d13]]"
exo__Asset_label: Общий хук перехватывает специфичный
aliases:
  - Общий хук перехватывает специфичный
  - generic hook blocks before specific one
  - два блока хуков подряд
  - совет верный вообще, неверный здесь
  - PreToolUse chain stops at first block
  - hook precedence
exo__Asset_isDefinedBy: "[[2ce77ac1-3f78-4f64-9dc1-41ea01da1ef0]]"
---

Симптом: на одну задачу пришло два блока подряд, и первый совет увёл не туда — цепочка PreToolUse останавливается на первом блоке, общий гвард стоит выше специфичного и даёт совет, верный вообще и неверный здесь. Специфичный детект ставить выше общего.

