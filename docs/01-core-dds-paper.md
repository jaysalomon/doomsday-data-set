# The Doomsday Data Set: a compact offline knowledge and intelligence system

## Abstract

The Doomsday Data Set (DDS) is a proposed open, highly compressed, model-agnostic knowledge base intended to preserve a useful working representation of human technical knowledge for local AI systems. Its aim is neither to archive the internet nor to retain millions of documents in their original publication form. Instead, DDS extracts useful information from books, manuals, papers, reference databases, and selected practitioner material; converts that information into compact machine-usable representations; validates those representations; and retains the compiled result as a versioned knowledge image.

Combined with a capable local language model, retrieval, structured databases, deterministic scientific and engineering tools, vision, CAD, and fabrication equipment, DDS can provide practical specialist assistance without an internet connection. The model does not need to memorise civilisation. Its job is to retrieve and reason over authoritative material, invoke deterministic tools where calculation is preferable to free-form prediction, state uncertainty and risk, and help a human make decisions.

## 1. Objective

The objective is simple:

> Preserve enough useful human knowledge that a capable local AI system can offer practical, specialist-level assistance when external information or specialists are unavailable.

This differs from both a conventional library and a huge language model. A conventional library stores documents. A language model stores an approximate statistical representation of information in its weights. DDS stores a compiled semantic representation: material that is searchable, inspectable, reconstructable, citable, and usable by tools.

The goal is not to claim certainty in every domain. It is to make the system better at finding the right references, carrying out checkable calculations, recognising uncertainty, and presenting a useful procedure than an isolated model operating from its weights alone.

## 2. The central idea: compile information, not files

A source document contains several different information types: prose, definitions, procedures, tables, equations, diagrams, photographs, charts, citations, and layout. The PDF or raster page is merely a human-facing container. DDS compiles each component into the smallest robust representation suited to its use.

```text
PDF prose              → structured Markdown with provenance
table or parts list    → typed records
chart                  → source values + plotting specification
schematic              → component graph + SVG + semantics
technical figure       → geometry + labels + rendering specification
procedure              → ordered, conditional steps + safety/verification checks
```

This can achieve much better compression than ZIP because DDS does not try to preserve every bit of the original artefact. It preserves the information required to recover its technical meaning and, where useful, render a clean replacement.

## 3. Knowledge packs and durability

DDS should be distributed as independently versioned packs such as Core Science, Engineering, Mechanics, Electronics, Computing, Agriculture, Food, Medicine, Robotics, and Field Notes. Each pack contains processed outputs, provenance, licenses, hashes, and manifests. Canonical compiled material is separate from derivative vector indexes because embeddings will age rapidly and vary by model.

The durable release is therefore the semantic corpus. A user can rebuild embeddings and indexes locally for a new inference profile without recompiling all knowledge. This also supports mirroring and distributed delivery: packs can be replicated via conventional downloads, torrents, or other content-addressed systems.

## 4. Ordinary runtime, unusually good inputs

DDS intentionally uses familiar runtime primitives:

```text
question
  → retrieve relevant compiled sources (RAG)
  → fetch exact records where necessary (DB)
  → run deterministic calculations, simulations, or renderers (tools)
  → model reasons over results and explains uncertainty
```

RAG is RAG; DB calls are DB calls; tool calls are tool calls. The distinctive work is upstream: converting a mountain of heterogeneous human information into a compact corpus that these ordinary mechanisms can use properly.

## 5. Local-first intelligence

DDS is model-agnostic. A local model is the normal private and offline default, but a router may use a stronger cloud model when the network exists and the user chooses it. In degraded operation, the same corpus, retrieval layer, structured data, and tools continue with local models alone.

The desired local-model behaviour is low refusal and high epistemic discipline. It must be able to discuss dangerous topics when doing so is needed for realistic diagnosis and risk management, while remaining anchored to sources, measurements, calculations, failure modes, and stated uncertainty. The human remains responsible for decisions and physical action.

## 6. From knowledge base to technical capability stack

At home-server scale, DDS can attach to a Python scientific environment, circuit simulation, CAD, Blender, computer vision, and workshop equipment such as a 3D printer, laser cutter, CNC machine, scanner, multimeter, oscilloscope, and thermal camera. The useful loop is:

```text
identify problem → retrieve → inspect → measure → calculate
→ design → simulate/check → manufacture → test → revise
```

This is not a chatbot with documents bolted on. It is a local technical-workflow system whose long-term knowledge is portable across models and hardware.

## 7. Development path

The home/server/workshop form is feasible now. The rugged low-power field workstation is a later packaging and efficiency problem: large memory, main inference, storage, multimodal inputs, substantial I/O, and a burst-capable compute layer must become practical in one battery-powered machine. The knowledge/compiler/toolchain built now should carry over nearly unchanged.
