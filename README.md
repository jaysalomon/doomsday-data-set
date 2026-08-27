# DOOMSDAY DATA SET (DDS)

DDS is a compact, model-agnostic, offline-capable technical knowledge system. It is not a conventional archive and it is not a model-training project. Its purpose is to compile high-value human knowledge into durable, machine-usable representations that can support local retrieval, database lookup, deterministic tools, and local or cloud inference.

The target system remains useful without internet access or cloud services, while still being free to use cloud models whenever connectivity is available. The durable asset is the compiled corpus and its reproducible build process; models, indexes, and hardware are replaceable layers.

## Workspace map

- [Core DDS paper](docs/01-core-dds-paper.md) — purpose, architecture, and working thesis.
- [Corpus taxonomy and acquisition](docs/02-corpus-taxonomy-and-acquisition.md) — what belongs in DDS and how it is selected.
- [Ingestion and compilation](docs/03-ingestion-and-compilation-pipeline.md) — source-to-pack build pipeline.
- [Visual reconstruction](docs/04-visual-reconstruction-pipeline.md) — image/text/SVG/semantic/reconstruction validation.
- [Model and inference profiles](docs/05-model-and-inference.md) — local low-refusal reasoning, RAG, DB, and tool calls.
- [Hardware architecture](docs/06-hardware-architecture.md) — home-server implementation through the later field system.
- [Design decisions](docs/00-design-decisions.md) — non-negotiable decisions carried over from the original discussion.

## First principle

```text
messy human source material
        ↓
DDS compiler
        ↓
compact, versioned knowledge packs
        ↓
ordinary RAG / database calls / tool calls
        ↓
replaceable local or cloud model
```

DDS is the compiler and the knowledge image. The inference plumbing is deliberately ordinary and replaceable.
