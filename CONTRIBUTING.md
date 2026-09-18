# Contributing to DDS

DDS is currently in an early architecture/prototype phase. Contributions are useful when they make the system more testable, reproducible or technically grounded.

## Good contribution areas

- rights-clear technical source sets for prototype packs;
- pack schemas and provenance metadata;
- extraction/compilation tooling;
- retrieval and reranking experiments;
- deterministic technical tools;
- evaluation tasks with explicit ground truth;
- model/quantisation comparisons;
- memory, latency and power measurements;
- visual reconstruction and validation methods;
- documentation that resolves a concrete architectural ambiguity.

## Before opening a large change

For substantial work, open an issue first describing:

1. the problem;
2. the proposed change;
3. how it can be tested;
4. any source-rights or redistribution constraints;
5. whether it changes a current design decision.

This avoids building around assumptions that conflict with the project’s core architecture.

## Evidence standard

DDS should distinguish clearly between:

- source-backed fact;
- measured result;
- deterministic calculation;
- model inference;
- design hypothesis.

Benchmark claims should include enough metadata to reproduce the run where practical.

## Source material

Do not add copyrighted source documents merely because they are technically useful. A prototype source set should be rights-clear for the intended use, and its provenance/licensing metadata should be recorded before compilation.

## Model and hardware claims

When adding a model or hardware profile, record at least:

- exact model/checkpoint;
- quantisation/compression format;
- runtime and version;
- context length used;
- hardware and memory;
- prompt/policy profile;
- benchmark version;
- latency and peak memory where measured.

Do not infer DDS suitability from a generic aggregate benchmark alone.

## Pull requests

Keep changes scoped. Explain what changed, why it matters, and how it was checked.

Where a change affects the corpus format, runtime boundary, validation rules or other architectural commitments, update the relevant design document as part of the same pull request.
