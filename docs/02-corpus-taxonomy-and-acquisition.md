# Corpus taxonomy and acquisition strategy

## Corpus tiers

1. **Authoritative reference** — standards where licensing permits, textbooks, peer-reviewed references, manufacturer manuals, service documentation, government/public-health guidance, and trusted data tables.
2. **Operational knowledge** — repair procedures, field guides, material/process guidance, diagnostic workflows, and domain-specific practitioner manuals.
3. **Practitioner supplement** — carefully selected forum discussions, field notes, and community material. These are useful for failure modes and real-world context, but must be explicitly lower-confidence and never silently elevated above primary references.
4. **Derived DDS material** — normalised procedures, structured tables, semantic visual specs, extraction tests, and cross-reference maps. These retain provenance to their sources.

## Initial pack taxonomy

- DDS Core: maths, physics, chemistry, biology, water, sanitation, agriculture, construction foundations.
- DDS Engineering: materials, mechanics, thermodynamics, machine design, controls, manufacturing.
- DDS Mechanics: engines, vehicles, bearings, pumps, hydraulics, pneumatics, repair procedures.
- DDS Electronics: circuits, wiring, RF, power electronics, embedded systems, diagnostics.
- DDS Computing: operating systems, networking, programming, electronics-adjacent tooling.
- DDS Medicine: first aid, clinical references, pharmacology, public health — governed by strict provenance and uncertainty rules.
- DDS Food: production, preservation, nutrition, recipes and process knowledge.
- DDS Robotics: sensors, actuation, control, machine vision, maintenance, field operation.
- DDS Field Notes: clearly labelled supplementary practitioner material.

## Acquisition rules

- Capture license, source identity, edition, publication date, jurisdiction, author/publisher, and retrieval date before compilation.
- Treat mutable, jurisdiction-specific, or high-stakes material as refreshable packages with explicit expiration/review metadata.
- Prioritise sources that support extraction into structured knowledge or have clear technical drawings, tables, procedures, and bibliographies.
- Preserve a private processing-side source ledger even where the final pack contains only compiled output.
- Never delete a source before all compiled artefacts have passed their pack-specific validation gates.

## Quality model

Every unit needs: provenance, subject taxonomy, version, confidence, applicable conditions, dependencies, extraction method, validation result, and a clear distinction between quoted/source fact, calculated result, and DDS inference.
