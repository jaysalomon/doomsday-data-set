# DDS design decisions

This file records the decisions already made. New work should extend them, not quietly substitute generic assumptions.

## Purpose and scope

- DDS preserves useful, working technical knowledge for use when connectivity, cloud services, or specialist access are absent.
- It is a semantic knowledge compiler, not a digital-library mirror and not an attempt to archive the internet.
- The working storage target is approximately 4 TB for the final compiled corpus. Raw sources and intermediate artefacts belong on separate processing storage.
- Knowledge packs, tools, corpus specifications, and hardware/model profiles should be separable and eventually open, versioned, and reproducible.

## Runtime boundary

- RAG retrieves relevant source-backed chunks.
- Database calls return structured facts and metadata.
- Tool calls perform deterministic work: calculations, simulations, plotting, CAD, OCR, rendering, and validation.
- The model reasons over the returned material. DDS does not require a novel inference framework.
- Local operation is the fallback guarantee, not a rule against using cloud models when they are useful.

## Visual knowledge

- Text, tables, charts, schematics, diagrams, and photographs are not treated as one image class.
- Structured visuals preserve exact text, explicit relationships, vector geometry where possible, and semantic rendering intent.
- A reconstructed visual need not mimic scanning artefacts, typography, or page texture. It must remain functionally equivalent.
- Deterministic rendering is preferred wherever the data permits it. Generative reconstruction is reserved for visual complexity that cannot be represented deterministically.
- Source deletion is allowed only after a tested semantic round trip meets the acceptance threshold.

## Model behaviour

- A DDS model should be low-refusal and able to reason about hazardous reality instead of replacing analysis with generic warnings.
- The desired property is **low refusal plus high epistemic discipline**, not reckless output.
- Functional safeguards are required: source grounding, uncertainty, unit checks, calculation verification, conflicting-source warnings, and explicit failure modes.
- Behavioural/product refusal policies are not the architecture's safety mechanism.

## Hardware direction

- Build the complete system as a home/server/workshop system first.
- A later field implementation should inherit the corpus, interfaces, tools, and workflows rather than become a separate product.
- Route each task to the lowest-power capable compute layer. Keep a separate higher-power CUDA/tensor worker for heavy on-demand jobs so main inference remains responsive.
