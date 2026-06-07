---
exo__Asset_uid: 53fc1bdf-814e-4816-8d4e-ecaf8c1bdf5d
exo__Asset_isDefinedBy: "[[2ce77ac1-3f78-4f64-9dc1-41ea01da1ef0]]"
exo__Asset_createdAt: 2026-05-17T20:24:37
exo__Asset_updatedAt: 2026-05-17T20:24:37
exo__Asset_createdBy: "[[de20a3f1-7483-4714-ab28-b45f5cf02c76|ExoAssistant]]"
exo__Instance_class:
  - "[[39a39239-2a97-483a-ba91-fb01bf5c85f3|aiKnow__MemoryReference]]"
exo__Asset_label: Backend IRI scheme post UID-canon — wikilink unwrap by filename only
aliases:
  - Backend IRI scheme post UID-canon — wikilink unwrap by filename only
exo__Asset_description: Backend @kitelev/exocortex-cli after UID-canon TBox enforcement emits ONLY obsidian:// IRIs for wikilink objects (unwrap by filename). Symbolic IRIs https://exocortex.my/ontology/<prefix>#<localname> are no longer emitted for UID-named TBox files. CQ writers must use obsidian://vault/<path>/<UID>.md form.
inbox__ExoAssistantKnowledge_decay: "[[06a5b9f9-da93-4234-883f-3f0cf65b2fba|aiKnow__DecayPermanent]]"
inbox__ExoAssistantKnowledge_confidence: "[[227def30-f56f-4f5f-936d-f6a81ad73c96|aiKnow__ConfidenceHigh]]"
inbox__ExoAssistantKnowledge_lastReinforcedAt: 2026-05-17T20:24:37
---

# Backend IRI scheme post UID-canon — wikilink unwrap by filename only

## Reference

После UID-canon TBox enforcement (RFC-004 follow-up, 2026-05-16) backend `@kitelev/exocortex-cli` парсер emits **только один** IRI для wikilink objects при unwrap'е:

- **Object IRI form (only):** `<obsidian://vault/<vault-path>/<UID>.md>`
- **NOT emitted:** symbolic form `<https://exocortex.my/ontology/<prefix>#<localname>>` — потому что UID-named TBox файлы не имеют symbolic local name резолвимого через `exo__Asset_label`.

## Implications для SPARQL / SHACL

- SPARQL CQs пишут IRI как `<obsidian://vault/assetspaces/<onto>/<UID>.md>`, **не** `<https://exocortex.my/ontology/exocmd#PropertyDefault>`. Symbolic form вернёт empty results.
- SHACL `--shapes-mode` использует obsidian:// IRI form для constraint validation.
- Subject IRI subjects (новые ассеты в vault) тоже используют obsidian:// form.

## Cross-vault SPARQL

Backend поддерживает multi-source через `--also <path>`. Cross-vault setup (vault-2025 + vault-exodev):

```bash
cd /Users/kitelev/vault-2025 && \
  npx @kitelev/exocortex-cli exoql query \
    --also /Users/kitelev/vault-exodev/inbox \
    --also /Users/kitelev/vault-exodev/assetspaces/exoass \
    --also /Users/kitelev/vault-exodev/assetspaces/exodev \
    '<SPARQL>'
```

## Empirical validation

- 2026-05-17 SPARQL Reviewer agent smoke test (4-agent RFC v2 review): 177173 triples loaded, cache 1.4s, query latency 2-28ms. Symbolic form `<ems#Task>` vs UID form `<obsidian://vault/.../1b20a8f0-...md>` дали **3 разных hits каждый** — non-equivalent extensions. Confirmed: post UID-canon только filename-based IRI.

## Applies when

- Writing onto-RFC Competency Questions
- Writing SHACL shapes targeting TBox classes
- Building SPARQL queries для KB introspection
- Cross-vault knowledge retrieval (multi `--also`)
