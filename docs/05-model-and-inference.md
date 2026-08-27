# Model and inference recommendations

## Design position

The DDS runtime is model-agnostic. It should accept a local open model as the default, optional cloud endpoints for difficult work, and specialist local vision/embedding/reranking models. The corpus format must outlive every model recommendation.

## Model requirements

- Strong instruction following, tool use, citation discipline, and context handling.
- Good technical reasoning relative to memory/power budget.
- Low refusal for legitimate hazardous-domain analysis, paired with explicit uncertainty and risk reasoning.
- Support for an offline, OpenAI-compatible local serving interface where practical.
- Quantisation and context profiles that are benchmarked against DDS tasks rather than generic leaderboards alone.

## Runtime responsibilities

```text
input/router
  → RAG retrieves relevant compiled chunks
  → DB queries fetch exact structured records
  → reranker selects evidence
  → main model reasons and chooses tools
  → tools return calculations, simulations, images, CAD, or checks
  → model presents result with provenance, uncertainty, and risk
```

RAG, DB, and tool calls remain separate mechanisms. Tool output is not treated as prose; it is labelled as a calculated or generated result.

## Functional safeguards

- Require retrieval for exact specifications and high-consequence claims.
- Make source quality and disagreement visible.
- Use unit-aware calculation, independent numerical checks, and range sanity checks.
- Separate fact, calculation, and inference in the final answer.
- Request or flag missing measurements rather than inventing them.
- Include failure modes, prerequisites, and residual risk where relevant.

## Tool environment

The local tool layer should include NumPy/SciPy, SymPy, pandas/Polars, Matplotlib, Pint, NetworkX, statsmodels/scikit-learn, control systems tooling, Cantera, RDKit, OpenCV, SPICE integration, and scriptable CAD/geometry tools. Use deterministic tools for deterministic work; do not ask the language model to simulate a circuit or silently calculate a safety-critical dimension in its head.

## Evaluation

Maintain DDS-specific benchmarks: retrieve a correct torque sequence; diagnose an electrical fault from supplied measurements; calculate and unit-check a beam/loading problem; identify a hazardous interaction from the sourced corpus; produce a valid schematic; and explain the answer with the relevant evidence. Score correctness, source use, tool choice, refusal rate, uncertainty calibration, and risk quality.
