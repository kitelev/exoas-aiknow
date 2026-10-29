---
exo__Asset_uid: f896ed21-fbee-4f60-8390-defc99dcfbd3
exo__Asset_createdAt: 2026-09-14T11:21:36
exo__Asset_updatedAt: 2026-10-29T14:19:50
exo__Instance_class:
  - "[[dda12c48-6886-4624-8710-ed4ba92ce2b3]]"
exo__Asset_createdBy: "[[4ef3962d-b8a7-42b5-bd28-88ec846f1d13]]"
exo__Asset_label: Wikilink на несуществующий файл (file not found in vault)
aliases:
  - Wikilink на несуществующий файл (file not found in vault)
  - Wikilink file not found in vault
  - validate-wikilinks blocked write
  - dangling wikilink
  - висячая ссылка на UID
  - ссылка не резолвится
  - broken wikilink
exo__Asset_isDefinedBy: "[[2ce77ac1-3f78-4f64-9dc1-41ea01da1ef0]]"
---

Симптом: CLI/хук отвечает `❌ Wikilink [[<uid>]] — file not found in vault`, либо ссылка в теле/frontmatter указывает на UID, которого в этом vault нет (вынесен в холодный архив, не смонтирован, угадан хвост UID). SHACL dangling-ссылку violation не считает — гейты молчат.

