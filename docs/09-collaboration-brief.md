# DDS collaboration brief

## What DDS is

The Doomsday Data Set is an open technical-systems research project aimed at compiling high-value human knowledge into compact, versioned, machine-usable packs for local retrieval, structured lookup, deterministic tools and replaceable AI models.

The central constraint is **degraded operation**: the system should remain useful when cloud services, internet access or specialist help are unavailable.

DDS is not trying to train a civilisation-scale foundation model. The corpus is external. The model is the reasoning and orchestration layer.

## What exists today

The project is currently at architecture/specification stage. The repository defines corpus boundaries and pack taxonomy, source and provenance requirements, canonical compiled representations, visual reconstruction and validation, the runtime split between RAG/databases/tools/model reasoning, hardware direction, and a DDS-specific evaluation methodology.

The next milestone is a bounded, reproducible prototype pack and evaluator.

## Why this may be useful to model and hardware teams

DDS provides a concrete workload for systems whose value depends on memory, latency, power and long-horizon reliability.

A DDS node needs more than short-form benchmark accuracy. It must retrieve authoritative evidence, maintain provenance, use tools over multiple dependent steps, handle missing or conflicting information, keep procedures coherent over long trajectories, distinguish fact from inference, and operate within a constrained local hardware budget.

That makes DDS a potentially useful external test bed for compressed models, inference runtimes and low-power accelerators.

## Proposed collaboration shape

A small technical collaboration could start with:

1. a fixed DDS benchmark pack;
2. a reference full/higher-precision model profile;
3. an unmodified compressed profile;
4. a DDS-adapted compressed profile where supported;
5. identical retrieval and tool infrastructure;
6. published per-task-family results.

The interesting outcome is not “our model scored X”. It is a measured capability-versus-footprint curve.

## What DDS can provide

As the prototype matures:

- domain-specific retrieval/tool-use trajectories;
- long-horizon procedural tasks;
- provenance-aware scoring;
- failure-recovery cases;
- conflicting-source tests;
- deterministic tool environments;
- reproducible profile metadata;
- real technical source material with clear ground truth where rights permit.

## What DDS would ask from a compression/model partner

- clarity on the adaptation-to-compression workflow;
- a reproducible inference artefact or build process;
- real resident-memory measurements;
- runtime/backend requirements;
- support for testing long-horizon regressions;
- permission to publish benchmark methodology and results;
- redistribution terms clear enough to define an open DDS model profile where possible.

## Immediate experiment

The most useful first experiment is intentionally narrow:

- one or two technical domains;
- 50–100 evaluation tasks;
- a mixture of retrieval, calculation, diagnosis and long procedures;
- one reference model and one highly compressed candidate;
- identical DDS corpus/tooling;
- full trajectory logs.

If the compressed model shows a large footprint reduction with acceptable long-horizon retention, the result directly informs the hardware design of later DDS nodes.

## Contact / project discussion

For now, collaboration can be coordinated through the GitHub repository via issues or discussions once enabled. A dedicated project contact can be added here when desired.
