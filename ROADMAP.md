# DDS roadmap

DDS is currently in the architecture and specification phase. This roadmap is deliberately staged so that each milestone produces something testable rather than merely expanding the design document.

## Phase 0 — specification

**Status: active**

- Define the durable corpus boundary.
- Define canonical representations.
- Define provenance and validation requirements.
- Define the runtime boundary between retrieval, databases, tools and model reasoning.
- Define evaluation metrics and profile metadata.
- Keep hardware and model choices replaceable.

**Exit condition:** another engineer should be able to understand what a DDS pack is, how it is built, how it is consumed and how success is measured.

## Phase 1 — minimal vertical slice

Build one bounded pack from rights-clear technical sources.

Suggested scope:

- one repair/engineering domain;
- text + tables + at least one structured visual class;
- provenance ledger;
- canonical compiled output;
- local retrieval;
- one structured database path;
- one deterministic calculation/tool path.

**Exit condition:** a user can ask real questions and the system can retrieve, calculate and cite through the complete DDS path.

## Phase 2 — evaluator

Create the first reproducible DDS benchmark:

- 50–100 tasks;
- explicit ground truth;
- short and long-horizon cases;
- retrieval, DB and tool-use scoring;
- uncertainty/conflict cases;
- raw trajectory logging;
- latency and memory measurements.

**Exit condition:** two different inference profiles can be compared reproducibly.

## Phase 3 — model/compression study

Compare:

- reference model;
- conventional quantisation;
- ultra-low-bit/ternary candidate;
- adapted candidate where available.

Publish per-family capability retention rather than a single aggregate score.

**Exit condition:** DDS has evidence for the minimum model/hardware class needed by the prototype.

## Phase 4 — multiple packs

Add additional domains and formalise:

- pack manifest schema;
- cross-pack references;
- pack update and deprecation rules;
- source refresh policy;
- reproducible index builds.

**Exit condition:** DDS is demonstrably a pack ecosystem rather than one bespoke demo.

## Phase 5 — hardware profiles

Benchmark complete DDS profiles across workstation/server, low-power local nodes, and portable/field-oriented hardware where practical.

Measure memory, latency, power, thermals and degraded-operation capability.

**Exit condition:** documented capability-per-watt and capability-per-cost profiles exist for realistic deployments.

## Phase 6 — field system

Only after the software/corpus stack is stable should DDS optimise towards a rugged field appliance.

The field system should inherit the same corpus, pack format, evaluator, tool interfaces, inference API and provenance model. It is a deployment profile, not a separate architecture.
