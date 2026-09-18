# DDS evaluation and benchmarking

## Purpose

DDS needs an evaluation suite that measures the behaviour the system actually depends on. Generic model leaderboards are useful background, but they do not tell us whether a model can reliably operate an evidence-grounded technical workflow.

The evaluator should compare complete DDS inference profiles against the same tasks, corpus snapshot and tool environment.

A profile includes:

- model and quantisation;
- context configuration;
- embedding and reranking stack;
- retrieval settings;
- available deterministic tools;
- prompt/system policy;
- hardware and runtime.

The unit of comparison is the **profile**, not the model name alone.

## Core task families

### 1. Retrieval and source selection

Examples include finding the correct torque sequence for a specified assembly, identifying the applicable wiring diagram from model/year/variant metadata, retrieving the right table row under stated conditions, and distinguishing manufacturer guidance from lower-confidence practitioner material.

Measure whether the correct evidence was found, ranked and cited.

### 2. Structured technical lookup

Examples include fetching component ratings from typed records, resolving part numbers and compatible variants, returning material properties with units and applicable conditions, and distinguishing jurisdiction-specific requirements.

The model should prefer exact database retrieval over free-form recall where the corpus provides structured data.

### 3. Calculation and tool use

Examples include beam/load calculations, voltage-drop checks, thermodynamic or fluid calculations, circuit simulation, CAD constraints, unit conversion and dimensional analysis.

Measure whether the model chooses the right tool, supplies valid inputs, interprets the output correctly and performs sanity checks.

### 4. Diagnosis from evidence

Examples include electrical fault diagnosis from measurements, mechanical failure diagnosis from symptoms and inspection results, process troubleshooting from observed values, and choosing the next discriminating measurement between competing explanations.

The target behaviour is iterative:

```text
evidence → hypothesis → missing information → measurement/tool
        → revised hypothesis → procedure/check
```

### 5. Procedural execution

Tasks should include multi-step procedures with prerequisites, branches, verification checks and explicit failure modes.

Measure step ordering, prerequisite recognition, branch selection, omission of critical checks, recovery after failed intermediate steps, and whether the model stops or asks for evidence when continuation would require invention.

### 6. Conflicting and incomplete evidence

Present sources with different revisions, conflicting practitioner and manufacturer guidance, missing measurements, ambiguous units, and stale or jurisdiction-specific advice.

The correct behaviour is not merely to pick one source. The system should expose the disagreement, identify the stronger evidence and state what remains unresolved.

### 7. Visual and multimodal technical reasoning

Where a DDS pack includes diagrams, charts, schematics or technical imagery, tasks should verify that the model can use the compiled visual representation correctly.

Examples include tracing a circuit path, identifying a component downstream of a fuse, reading an exact chart value, inferring assembly order from an exploded drawing, and recognising when a photograph contains evidence that was not preserved by an abstract reconstruction.

## Metrics

At minimum record:

- task correctness;
- evidence retrieval accuracy;
- citation/source correctness;
- unsupported-claim rate;
- tool-choice accuracy;
- tool-call success rate;
- unit and numerical error rate;
- uncertainty calibration;
- conflict handling;
- refusal/abstention rate;
- unnecessary refusal rate;
- recovery after tool or retrieval failure;
- tokens generated;
- latency;
- peak memory/VRAM;
- energy use where measurable.

For long-horizon tasks also record **trajectory success**: whether the whole sequence reaches a correct outcome, not just whether individual turns look plausible.

## Compression evaluation

Compression should be judged against a full-precision or higher-precision reference model on exactly the same DDS suite.

Report both absolute performance and retention:

```text
retention = compressed_profile_score / reference_profile_score
```

Do not collapse every task into one aggregate. Publish per-family results, especially for long-horizon procedural work, tool orchestration, retrieval recovery, multimodal reasoning, and uncertainty/conflict handling.

A model can retain almost all short-task accuracy while losing materially more capability on long trajectories. DDS should make that visible.

## Evaluation artefacts

Every published run should record:

- DDS corpus/pack version;
- benchmark version;
- model artefact and hash;
- runtime/quantisation;
- prompt/policy version;
- tool versions;
- hardware;
- deterministic seeds where applicable;
- raw task outputs;
- scoring code.

The goal is a reproducible technical benchmark, not a screenshot of a leaderboard.

## Initial milestone

The first public evaluator can be small: roughly 50–100 high-quality tasks across two or three technical domains, with a mixture of single-step and long-horizon cases.

A small benchmark with strong ground truth and reproducibility is more useful than a large benchmark whose scoring is vague.
