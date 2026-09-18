# Model adaptation and compression

## Position

DDS is designed so that domain knowledge remains in the corpus rather than being baked permanently into model weights.

Model adaptation should therefore primarily improve **how the model operates DDS**:

- retrieve before guessing;
- distinguish source fact, calculation and inference;
- use deterministic tools correctly;
- reason over conflicting evidence;
- request missing measurements;
- preserve provenance;
- follow long technical procedures;
- recover after failed retrieval or tool calls;
- discuss hazardous reality without replacing analysis with generic refusal language.

The objective is not to turn the model into a lossy copy of the corpus.

## Why ultra-low-bit models are relevant

The model is a replaceable reasoning layer, so memory saved in model weights directly improves the feasible DDS hardware envelope.

If a capable 20–30B-class model can run in roughly the memory footprint normally associated with a much smaller model, DDS gains headroom for KV cache and longer contexts, vision encoders, rerankers and embedding models, resident structured databases, concurrent tools, lower-cost GPUs or unified-memory systems, and lower-power field hardware.

For DDS, model compression is therefore not merely a deployment optimisation. It can change the class of machine on which the whole system is practical.

## Candidate adaptation workflow

A useful collaboration should be able to test a pipeline broadly like:

```text
base model
  → DDS behavioural / tool-use post-training
  → compression / ternarisation / quantisation
  → DDS evaluator
```

and, where supported:

```text
base model
  → compression-aware adaptation
  → compressed DDS profile
  → DDS evaluator
```

The key question is whether specialist behaviour survives the compression process at the target footprint.

DDS should not assume that a technique demonstrated on a base model can automatically be applied after arbitrary fine-tuning. That needs to be tested.

## What the training data should teach

Post-training examples should focus on trajectories, not factual memorisation.

Useful classes include:

1. **Retrieve, then answer** — exact technical values must come from supplied evidence.
2. **Retrieve again** — the first retrieval is incomplete or ambiguous.
3. **Use a tool** — calculation or simulation is explicitly delegated.
4. **Reject a bad tool result** — unit mismatch, impossible range or malformed input.
5. **Resolve conflict** — sources disagree and the model must identify revision, authority or applicable conditions.
6. **Ask for a measurement** — the next step cannot be determined from current evidence.
7. **Long procedure** — preserve state over many dependent steps.
8. **Failure recovery** — a step fails and the model chooses an alternative diagnostic path.
9. **Risk reasoning** — identify failure modes, consequences and controls while still answering the underlying technical question.
10. **Abstain precisely** — say exactly what cannot be concluded and what evidence would resolve it.

## Benchmark comparison

Every adapted model should be compared against at least:

- the unmodified base model;
- the same base model at a conventional quantisation level;
- the target ultra-low-bit/compressed model;
- the adapted compressed model.

This separates gains from adaptation, losses from compression, gains that survive compression, and regressions specific to long-horizon operation.

## Collaboration questions for model-compression teams

DDS is particularly interested in answers to the following:

1. Can a domain-adapted checkpoint be converted to the same compressed format as the released base model?
2. Does the conversion require access to the original training pipeline or only the adapted weights?
3. What calibration data is required?
4. Does post-training need to happen before or after compression?
5. Which layers or tensors remain at higher precision?
6. What is the true resident memory footprint at useful context lengths?
7. Which runtimes and accelerator backends are supported?
8. How much performance is lost specifically on long-horizon tool-use tasks?
9. Can compression-aware training recover that loss?
10. Can the resulting artefact and runtime be redistributed under terms compatible with an open DDS profile?

## Candidate: ternary 20–30B-class inference

Recent ternary and near-ternary post-training compression work is especially relevant to DDS because it targets large reductions in resident weight memory while retaining much of the source model's capability.

DDS should treat any specific model or vendor as an **evaluation candidate, not an architectural dependency**. The correct test is straightforward:

> Does the compressed profile retain the evidence-grounded, tool-using, long-horizon behaviour DDS needs at a materially better memory, latency or power point?

The answer should come from the DDS evaluator rather than generic aggregate benchmarks.
