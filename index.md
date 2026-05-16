---
exo__Asset_uid: 78366774-d1f5-4e26-8d70-0930380bb6df
exo__Asset_isDefinedBy: "[[!aiKnow-as]]"
exo__Instance_class:
  - "[[exo__AssetSpace]]"
exo__AssetSpace_namespace: "https://exo.ai/aiknow#"
exo__AssetSpace_version: "0.1.0"
exo__AssetSpace_type: "ontology"
exo__AssetSpace_gitRemote: "git@github.com:kitelev/exocortex-aiknow-ontology.git"
---
# exocortex-aiknow-ontology

aiKnow ontology TBox: classes and properties for AI knowledge management in Exocortex.
Part of [Exocortex](https://github.com/kitelev/exocortex) ecosystem.

## Classes

- `aiKnow__MemoryFeedback` — behavioral lessons / corrections / preferences
- `aiKnow__MemoryReference` — stable factual references, API/config pointers
- `aiKnow__MemoryProject` — project-history memories, closure reports
- `aiKnow__BehavioralRule` — always-load rules injected on every UserPromptSubmit

## Properties

- `aiKnow__Memory_aboutConcept` — links memory to ims__Concept instances
- `aiKnow__MemoryProject_doneAt` — timestamp property for project memory decay
