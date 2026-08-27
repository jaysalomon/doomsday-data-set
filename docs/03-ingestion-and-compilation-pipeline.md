# Ingestion and compilation pipeline

## Pipeline overview

```text
acquire + license/provenance record
  → classify source and page regions
  → extract text, tables, equations, and visuals
  → compile each type to its canonical form
  → link claims, artefacts, and source locations
  → validate content and functional reconstruction
  → package, hash, version, and index
```

## Canonical representations

- Prose: structured Markdown with headings, defined terms, citations, units, conditions, and source locators.
- Procedures: numbered actions, prerequisites, decision branches, measurements, tools, acceptance checks, and failure modes.
- Tables: typed CSV/JSON/SQLite records, not screenshots.
- Equations: machine-readable mathematical notation plus definitions and units.
- Charts: values, axes, units, series, annotations, and deterministic plotting specification.
- Technical diagrams: graph/structured data, SVG where possible, exact labels, and semantic rendering specification.
- Photographs: retained or compiled according to whether exact appearance is evidence; see the visual pipeline.

## Validation gates

1. Provenance and rights recorded.
2. Extraction completeness checked against the source.
3. Textual, numerical, and unit validation.
4. Cross-reference integrity and duplicate/conflict detection.
5. Artefact-specific functional validation, including visual round trips where applicable.
6. Human review for high-consequence or low-confidence content.
7. Signed manifest and content hashes before release.

## Source lifecycle

Raw material is processing input, not final DDS content. It is retained while the compiler and validators need it, then handled according to rights, preservation requirements, and the pack's accepted validation policy. The final drive contains compiled knowledge, package manifests, and enough provenance to assess claims; it is not assumed to contain every original PDF or image.
