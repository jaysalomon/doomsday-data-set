# Proposed DDS × Bonsai evaluation

## Purpose

This document defines a concrete experiment for evaluating a highly compressed 20–30B-class model as the reasoning layer of DDS.

The immediate candidate is PrismML’s Ternary Bonsai 2 27B family. The experiment is intentionally framed so that the same protocol can later be applied to other compressed models.

The question is not whether a compressed model retains a high aggregate benchmark score.

The question is:

> Can it retain enough evidence-grounded, tool-using, long-horizon technical behaviour to make a materially smaller and lower-power DDS node practical?

## Experimental profiles

At minimum compare:

1. **Reference profile** — the corresponding higher-precision base model.
2. **Conventional quantised profile** — a practical 4-bit-ish deployment where available.
3. **Bonsai profile** — the released compressed model.
4. **DDS-adapted Bonsai profile** — if a supported post-training/compression workflow exists.

Everything else should remain as identical as possible:

- same DDS pack;
- same retrieval results;
- same tool APIs;
- same task definitions;
- same scoring;
- same context budget where technically feasible.

## Task groups

### Retrieval-grounded technical answers

The model must use supplied DDS evidence for exact specifications, procedures and source-sensitive claims.

Failure modes to measure:

- answering from memory instead of retrieval;
- citing the wrong source;
- inventing an exact value;
- failing to notice source revision/variant differences.

### Multi-step diagnosis

The model receives incomplete observations and must choose the next discriminating measurement or lookup.

The benchmark should reward efficient evidence gathering, not merely a plausible final guess.

### Deterministic tool orchestration

Tasks should require calculations, simulations or structured database calls.

The model must:

- select the right tool;
- provide valid inputs;
- inspect units/ranges;
- reject impossible outputs;
- incorporate the result into the next step.

### Long-horizon procedures

Use procedures with dependencies, branches, state changes and verification steps.

This is a critical test for extreme compression because a model can preserve short-answer accuracy while degrading on trajectory coherence.

### Conflicting evidence

Provide sources with different revisions, authority or conditions of applicability.

The model should identify the disagreement rather than smoothing it into a single unsupported answer.

### Recovery tests

Deliberately inject:

- a failed tool call;
- an empty retrieval;
- an irrelevant top retrieval;
- a unit mismatch;
- a contradictory measurement.

Measure whether the model recovers or compounds the error.

## Metrics

Publish per task family:

- full-task success;
- source/citation correctness;
- unsupported-claim rate;
- tool-choice accuracy;
- tool-call validity;
- recovery rate;
- unit/numerical errors;
- uncertainty calibration;
- unnecessary refusal rate;
- median and tail token usage;
- latency;
- peak resident memory/VRAM;
- energy use where measurable.

Do not present only one aggregate retention number.

## Post-training target

If collaboration permits a DDS-specific adapted checkpoint, the training target should be behaviour rather than corpus memorisation.

Priority behaviours:

- retrieve before asserting exact values;
- retrieve again when evidence is incomplete;
- ask for missing measurements;
- keep source fact separate from inference;
- use deterministic tools;
- maintain procedural state over long trajectories;
- detect malformed tool outputs;
- expose source conflict;
- describe risk and failure consequences without abandoning the technical task.

## Questions for PrismML

A useful technical discussion would establish:

1. whether an adapted Qwen-family checkpoint can be passed through the Bonsai compression pipeline;
2. whether adaptation should happen before or after ternarisation;
3. whether compression-aware post-training is available;
4. what calibration/training data is required;
5. what model components remain above ternary precision;
6. what the real runtime memory footprint is once context/KV cache is included;
7. which backends are suitable for Intel Arc/Vulkan and other low-cost hardware;
8. whether custom compressed artefacts can be redistributed;
9. whether PrismML would be interested in evaluating long-horizon DDS trajectories as an external benchmark.

## Success criterion

The experiment succeeds if it produces a reproducible capability-versus-footprint curve.

A useful outcome does not require the compressed model to match the reference model everywhere. If it materially reduces memory/power while retaining enough end-to-end DDS task success, it can still be the better system component.

Conversely, strong short-form benchmark retention should not count as success if long-horizon DDS trajectories fail disproportionately.
