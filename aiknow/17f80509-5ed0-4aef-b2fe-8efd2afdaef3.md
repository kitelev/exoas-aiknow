---
exo__Asset_uid: 17f80509-5ed0-4aef-b2fe-8efd2afdaef3
exo__Asset_createdAt: 2026-09-14T12:02:48
exo__Asset_updatedAt: 2026-10-29T13:18:33
exo__Instance_class:
  - "[[dda12c48-6886-4624-8710-ed4ba92ce2b3]]"
exo__Asset_createdBy: "[[4ef3962d-b8a7-42b5-bd28-88ec846f1d13]]"
exo__Asset_label: Усечённый UID в теге или ссылке
aliases:
  - Усечённый UID в теге или ссылке
  - "@req tag truncated to 8 chars"
  - 8-char UID prefix instead of full UUID
  - REQ_TAG_RE не матчит короткий UID
  - укороченный UID не резолвится
  - хвост UID дописан по памяти
exo__Asset_isDefinedBy: "[[2ce77ac1-3f78-4f64-9dc1-41ea01da1ef0]]"
---

Симптом: тег/ссылка выглядит валидно, а гейт или валидатор краснит — UID усечён до 8 символов (`@req:ec019a32`) либо хвост дописан по памяти; регэксп ждёт полный UUID, wikilink-валидатор не находит файл. Полный UID брать из `find`/выдачи, не из прозы.

