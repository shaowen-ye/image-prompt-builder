# Template — Scientific Illustration

Use this template for **scientific illustrations**: habitat cross-sections (river, lake, forest, soil profile), life cycles, anatomical diagrams, mechanism diagrams (food web schematics — not topologies, see warning — biogeochemical cycle illustrations).

The defining feature: the illustration depicts a **conceptual or biological system**, not a data set. There is room for visual interpretation — a "river cross-section" doesn't need to be a specific real river — but morphology and proportions matter, and labels usually accompany.

## Contents

- What this template is not for
- Structural elements to capture
- Prompt skeleton — ChatGPT/OpenAI GPT Image
- Prompt skeleton — Gemini/Nano Banana
- Watch out for
- Post-processing notes

## What this template is NOT for

- **True food-web topologies based on real interaction matrices** → red-line, use cheddar / igraph.
- **Maps showing real geographic features** → red-line, use QGIS.
- **Statistical relationships visualized as figures** → red-line, use R/Python.

The skill's red-line check should catch these before you reach this template. If unsure, ask the user: "Does this need to represent a specific real dataset, or is it a conceptual / typical-case illustration?" Conceptual → proceed; real-data → redirect.

## Structural elements to capture

1. **What system / scene** — "alpine river pool-riffle sequence", "Microcystis colony with gas vesicles", "wetland nitrogen cycle".
2. **Viewpoint** — cross-section (vertical slice) / longitudinal section / plan view (top-down) / isometric / oblique perspective / scientific-plate style (multiple labeled elements arrayed).
3. **Key features to include** — list the specific elements: substrate, flow direction, organisms, gradients, transitions.
4. **Labels strategy** — labels drawn in the image / placeholder boxes where labels will be added in post / no labels at all.
5. **Style** — flat 2D educational / scientific plate (mid-century journal) / watercolor naturalist / technical line drawing / 3D isometric / cross-section with cutaway.
6. **Specificity** — generic-typical / regionally-specific (this can be risky; image models may not render regional species accurately).

## Prompt skeleton — ChatGPT/OpenAI GPT Image

```
A [style direction] scientific illustration depicting [system / scene], viewed [viewpoint].

COMPOSITION:
- [Region/element 1]: [what is shown, with morphological specifics]
- [Region/element 2]: [what is shown]
- [Region/element 3]: [what is shown]

KEY MORPHOLOGICAL FEATURES (render accurately):
- [Feature 1, with specifics, e.g., "boulder-cobble substrate, mixed sizes 5-30 cm, angular fragments"]
- [Feature 2]
- [Feature 3]

LABELS:
- [Either: "Show numbered label markers (1)-(N) at: [positions]. Do not render label text."
   Or: "Render labels exactly as quoted: '[label 1]', '[label 2]', '[label 3]'."
   Or: "No labels — clean illustration only."]

STYLE:
- [color palette, line weight, level of detail]
- [reference visual idiom, e.g. "mid-century natural science journal plate", "flat 2D educational textbook"]
- Avoid: photorealistic textures, glowing effects, atmospheric blur, decorative elements unrelated to the system.

ASPECT RATIO: [ratio]
INTENDED USE: figure in a [research paper / textbook / report / presentation]
```

### Example — ChatGPT/OpenAI GPT Image prompt for a river habitat cross-section

Brief: a river pool-riffle sequence cross-section for a freshwater ecology research report, showing substrate gradient, flow regime, and typical habitat features. No labels in image — will be added in post.

```
A flat 2D scientific illustration depicting a mountain stream habitat showing a pool-to-riffle transition, viewed as a longitudinal cross-section (side view, vertical slice through the water column).

COMPOSITION:
- Left third: deep pool with calm, layered water surface, fine sediment and silt on the bed
- Middle third: transitional zone — water shallows, surface develops gentle ripples, substrate transitions from sand to small gravel
- Right third: shallow riffle with turbulent broken-water surface, substrate of cobbles and boulders (5-30 cm diameter, angular fragments)

KEY MORPHOLOGICAL FEATURES (render accurately):
- Flow direction arrows: subtle horizontal arrows in the water column, indicating left-to-right downstream flow
- Substrate gradient: clearly different size and angularity from left (fine, rounded) to right (coarse, angular)
- Water surface: smooth on left, broken white on right
- A few small generic fish silhouettes — not species-specific — positioned naturally: 2 in the pool depth, 1 in transitional zone, 0 in the turbulent riffle
- Riparian vegetation hint at the top edge: simple plant silhouettes, not detailed
- No people, no built structures

LABELS:
- Show numbered label markers (1), (2), (3), (4), (5) as small black-outlined white circles at: (1) pool surface, (2) pool substrate, (3) transitional zone, (4) riffle substrate, (5) riffle water surface.
- Do not render any label text — labels will be added in post.

STYLE:
- Color palette: muted teal-blue water with subtle gradient (darker in pool, lighter in riffle), warm sand-tan substrate transitioning to gray-brown rock, soft sage riparian
- Flat 2D educational illustration style with clean line work, no photorealistic texture
- Mid-century natural science journal plate aesthetic — confident, restrained, slightly textured printed feel
- Avoid: photorealistic water reflections, glowing effects, atmospheric blur, decorative elements, drop shadows, glossy 3D look

ASPECT RATIO: 16:9 landscape (figure-in-paper format)
INTENDED USE: methods-section figure in a freshwater ecology research report
```

## Prompt skeleton — Gemini/Nano Banana

```
A scientific illustration in the style of [style reference], showing [system / scene] in [viewpoint]. The image is intended as a figure in [use context].

The scene unfolds [spatially]. On [side / region], [element with morphological detail]. [Continue spatial walk-through naming key features with their specifics — substrate types, flow regime, organisms, transitions].

[If labels needed]: small numbered markers appear at [positions]; the labels themselves will be added later.

The illustration is rendered [style description as visual language]. The palette is [colors named as feelings, not just hex]. Light is [direction and quality]. The medium feels like [print medium reference].

Avoid [photorealism / drop shadows / decorative elements].

Aspect ratio: [ratio].
```

### Example — Gemini/Nano Banana prompt (same brief as the OpenAI example above)

```
A scientific illustration in the style of a mid-century natural science journal plate, showing a mountain stream habitat transitioning from a deep pool to a shallow riffle, viewed as a longitudinal cross-section through the water column. The image is intended as a methods-section figure in a freshwater ecology research report.

The scene unfolds left to right. On the left, a deep pool with calm layered water surface and fine silt-sand bed. In the middle, the water shallows and the surface develops gentle ripples; the substrate transitions from sand to small gravel. On the right, a shallow riffle with broken white turbulent surface flowing over a substrate of angular cobbles and boulders, five to thirty centimeters across. Subtle horizontal arrows in the water column indicate downstream flow.

A few small generic fish silhouettes appear naturally placed — two resting in the pool depth, one in the transitional zone, none in the turbulent riffle. The top edge of the frame shows a hint of riparian vegetation as simple plant silhouettes, no detail. No people, no built structures.

Five small numbered marker circles (1) through (5) appear at the pool surface, pool substrate, transitional zone, riffle substrate, and riffle water surface. The label text itself is not drawn — the markers are placeholders.

The illustration is rendered in clean flat lines with no photorealistic texture. The palette is restrained: muted teal-blue water, slightly darker in the pool and brighter in the riffle, warm sand-tan substrate giving way to gray-brown rock, soft sage in the riparian band. Light is even and diffuse, like daylight on a printed page. The medium feels like high-quality printing on uncoated paper with subtle ink variation.

Avoid photorealistic water reflections, glowing effects, atmospheric blur, drop shadows, glossy 3D rendering, or decorative flourishes.

Aspect ratio: 16:9 landscape.
```

## Watch out for

- **Species-specific anatomy**: if the user needs a specific species (e.g. a particular *Microcystis* species, a specific fish), the model will render *something fish-like* or *something colony-like*, but morphological accuracy is unreliable. Tell the user; suggest generating a "generic representative" and then redrawing taxonomic details by hand if accuracy matters.
- **Scale accuracy**: relative sizes are approximate. If the figure needs accurate scale (e.g. "the cobble should be twice the diameter of the gravel"), state it explicitly and verify in output.
- **Anatomical structures**: organs, tissues, cell components — image models pattern-match on visual familiarity. For anatomical teaching materials, use the image as a base sketch and have a human illustrator finalize.
- **Cross-section conventions**: image models sometimes draw cross-sections inconsistently (mixing side-view and plan-view in one figure). Specify the viewpoint clearly.

## Post-processing notes to surface

- **Morphology**: verify every named feature against a reference.
- **Proportions**: measure or visually check relative sizes against the brief.
- **Labels**: if generated, check spelling; if placeholders, add in vector editor.
- **For publication**: this template's outputs are usually starting points. For peer review, redrawing in Illustrator gives you control over labels, vector scalability, and accuracy. Use the model output as visual reference, not as final figure.
