# Visual knowledge compilation and reconstruction pipeline

## Purpose

DDS treats many images as compiled visual information rather than permanent raster artefacts. A large electrical schematic may contain only component identities, values, connection topology, labels, arrows, and a small amount of geometry. The pixels are one rendering of that information, not the information itself.

```text
original image
  → visual classification + OCR/layout extraction
  → semantic specification + exact text + structural data + geometry
  → deterministic or constrained reconstruction
  → functional comparison with original
  → refinement
  → validated DDS representation
```

The system separates **meaning**, **geometry**, and **rendering**.

## 1. Document and text extraction

At page level, identify body text, headings, captions, tables, equations, labels, callouts, footnotes, figure references, diagrams, photos, charts, maps, exploded views, and schematics. Extract text directly wherever possible. A diagram label such as `F27 — 15 A` must become an exact structured value, not merely a visual path that resembles text.

## 2. Visual classification

Choose the representation by visual class: electrical/wiring/hydraulic/pneumatic schematic; mechanical exploded or assembly drawing; flow/block diagram; technical illustration; chart; map; labelled or unlabelled photograph; microscopy or diagnostic imagery; or generic illustration. A wiring diagram is primarily topological. A photograph showing corrosion may need richer visual evidence and may not be eligible for aggressive abstraction.

## 3. Semantic extraction

The result is not a vague caption. It is a machine-readable rendering and interpretation specification: objects, relationships, relative positions, labels, numerical values, flow directions, dimensions, coded colours, and annotations. It must also state what is critical and what is cosmetic.

```yaml
critical:
  - connection topology
  - component names and values
  - flow and arrow direction
  - measurements and units
non_critical:
  - paper texture
  - brand logo
  - exact typeface
  - scan blemishes
```

## 4. Structural and vector representation

Where possible, store SVG for visible geometry and structured data for relationships. For example, a schematic's component graph records IDs, types, terminals, ratings, and connections. SVG preserves positions, paths, arrows, callouts, and label anchors. Semantic description records interpretation and rendering intent. No one representation substitutes for the others.

## 5. Reconstruction

Use deterministic reconstruction when possible: charts from data, schematic SVG from a graph, maps from vector data, tables from records. For visuals that need generative rendering, use the structural data and SVG as constraints, with a rendering specification that names exact labels, count and relationships of components, orientation, colour meaning, legends, and prohibitions on adding or removing functional content.

The reconstruction engine must receive the compiled representation, not the original image. Otherwise the round trip proves nothing.

## 6. Functional validation

Do not use pixel similarity as the primary metric. A clean new wiring schematic can be functionally superior to a degraded 1987 scan. Ask instead:

- Are all meaningful objects present?
- Are labels and numerical values exact?
- Are all connections and arrow directions correct?
- Are spatial relations and dimensions preserved where they affect interpretation?
- Has anything meaningful disappeared or been invented?
- Could a competent user reach a different technical conclusion?

The acceptance criterion is functional equivalence.

## 7. Generated visual tests

Generate question sets that depend on the original visual, then answer them independently using the source and compiled reconstruction. For a schematic: what is connected downstream of fuse F27, what is F27's rating, which relay terminal supplies motor M1, and where does M1 negative connect? Disagreement is evidence of lost information.

## 8. Iterative refinement and source deletion

```text
extract → describe → vectorise → reconstruct → compare
       → identify mismatch → refine → repeat
```

Only when textual, structural, semantic, and functional tests pass may the compiled visual receive its confidence score and become eligible for source deletion under the source-lifecycle policy. Originals remain on processing storage while this happens; they are not assumed to belong on the final DDS drive.

## Worked classes

- **Charts:** extract data, axes, units, series, annotations, and plotting specification; rerender deterministically.
- **Exploded mechanical drawings:** retain SVG geometry, part IDs, assembly order, adjacency, fasteners, orientation, and insertion direction. The compiled output can enable highlighting, translation, simplified repair diagrams, or assembly animation.
- **Photographs:** compile objects, condition, viewpoint, geometry, OCR, damage, meaningful colour and texture, and critical visual evidence. Retain source imagery when exact visual details are themselves evidentiary or cannot yet be validated through reconstruction.
