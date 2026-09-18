# DOOMSDAY DATA SET (DDS)

**DDS is a model-agnostic, offline-capable technical knowledge system designed to preserve useful human knowledge as compact, inspectable, machine-usable data.**

It is not an internet archive, a conventional document dump, or a project to train a foundation model. DDS treats source material as compiler input: prose, procedures, tables, equations, diagrams, charts and selected imagery are transformed into versioned knowledge packs with provenance, validation metadata and deterministic representations wherever possible.

The long-term aim is practical: a local system should still be able to retrieve evidence, reason over it, run calculations and tools, and support technical work when internet access, cloud services or specialist help are unavailable.

> **Project status:** architecture and specification phase. The repository currently defines the corpus model, compilation pipeline, runtime boundary, evaluation strategy and hardware direction. It does not yet contain a production DDS release pack.

## Core idea

```text
messy human source material
        ↓
DDS compiler
        ↓
compact, versioned knowledge packs
        ↓
RAG / database queries / deterministic tools
        ↓
replaceable local or cloud model
```

The durable asset is the compiled corpus and reproducible build process. Models, embeddings, indexes and hardware are replaceable layers.

## What makes DDS different

- **Compile information, not files.** Preserve technical meaning rather than page texture or publication layout.
- **Keep provenance first-class.** Claims, tables, procedures and visuals remain linked to source identity and location.
- **Separate deterministic work from model judgement.** Calculations, simulations, unit checks, plotting and structured lookups should be done by tools where possible.
- **Treat uncertainty explicitly.** The system should distinguish source fact, calculated result, inference, disagreement and missing information.
- **Remain model-agnostic.** A stronger model can be swapped in without rebuilding the knowledge base.
- **Remain useful offline.** Cloud access is optional acceleration, not an architectural dependency.

## Why model compression matters

DDS is deliberately designed so that the model does **not** need to memorise the corpus. The model is the reasoning and orchestration layer over retrieved evidence and tools.

That makes low-memory, high-capability inference especially valuable. A compressed 20–30B-class model that can operate within a small VRAM or unified-memory budget could materially reduce the cost, power and size of a DDS node.

For that reason DDS will benchmark model families and compression methods against DDS-specific tasks rather than relying on generic leaderboard averages alone. See:

- [Model adaptation and compression](docs/08-model-adaptation-and-compression.md)
- [Evaluation and benchmarking](docs/07-evaluation-and-benchmarking.md)

## Repository map

- [Design decisions](docs/00-design-decisions.md) — non-negotiable architectural choices.
- [Core DDS paper](docs/01-core-dds-paper.md) — purpose, architecture and working thesis.
- [Corpus taxonomy and acquisition](docs/02-corpus-taxonomy-and-acquisition.md) — what belongs in DDS and how it is selected.
- [Ingestion and compilation](docs/03-ingestion-and-compilation-pipeline.md) — source-to-pack build pipeline.
- [Visual reconstruction](docs/04-visual-reconstruction-pipeline.md) — semantic extraction, deterministic reconstruction and validation.
- [Model and inference](docs/05-model-and-inference.md) — local reasoning, retrieval, database and tool boundaries.
- [Hardware architecture](docs/06-hardware-architecture.md) — home/server implementation through later field systems.
- [Evaluation and benchmarking](docs/07-evaluation-and-benchmarking.md) — task families, metrics and comparison methodology.
- [Model adaptation and compression](docs/08-model-adaptation-and-compression.md) — how specialist post-training and ultra-low-bit inference fit DDS.
- [Collaboration brief](docs/09-collaboration-brief.md) — what DDS can offer research and systems collaborators.
- [Roadmap](ROADMAP.md) — staged path from specification to reproducible prototype.

## First implementation target

The first serious DDS prototype should prove the whole loop on a bounded technical domain:

1. acquire a small, rights-clear source set;
2. compile it into canonical DDS representations;
3. build retrieval, structured lookup and deterministic tool paths;
4. evaluate at least two local model profiles against the same task suite;
5. measure source use, correctness, tool choice, uncertainty and failure recovery;
6. publish the pack format, evaluator and reproducible build process.

The first prototype is therefore not “a chatbot over PDFs”. It is a test of whether a compact semantic corpus plus a replaceable model can outperform an isolated model while remaining inspectable and reproducible.

## Collaboration

DDS is particularly interested in work on:

- compact local reasoning models;
- post-training for evidence-grounded tool use;
- ultra-low-bit and ternary inference;
- retrieval and reranking under tight memory budgets;
- robust long-horizon procedural reasoning;
- semantic document and diagram compilation;
- low-power local inference hardware;
- reproducible technical evaluation.

See the [collaboration brief](docs/09-collaboration-brief.md) for the concrete questions and interfaces.

## Licensing and source rights

DDS source acquisition and redistribution must follow the rights of each underlying source. Compiled packs therefore need explicit provenance and licensing metadata at pack and item level.

A repository-wide software/data licence has **not yet been declared** here. That decision should be made explicitly before releasing code or compiled corpus artefacts beyond documentation.
