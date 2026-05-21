# Template — Process Diagram / Flowchart

Use this template when the user wants a **process flow, framework diagram, or technical schematic**: monitoring–restoration–evaluation loops, decision trees, multi-step workflows, system architecture sketches.

## Contents

- First step — consider Mermaid instead
- When to proceed with image generation
- Structural elements to capture
- Prompt skeleton — ChatGPT/OpenAI GPT Image
- Prompt skeleton — Gemini/Nano Banana
- Watch out for
- Post-processing notes

## First step — consider Mermaid instead

Process diagrams are **the figure type most often better handled by Mermaid or draw.io**, not by image generation. Before writing an image prompt, ask:

- Will the user need to **edit this diagram later**? → Mermaid wins (editable, version-controllable forever).
- Are there **specific node labels and connection labels** that must be exactly right? → Mermaid wins (text is canonical, no risk of hallucination).
- Does the diagram need to **integrate with other documents** as vector / SVG? → Mermaid wins (clean vector output).
- Is this for an **internal working document**? → Mermaid is usually fine and faster.

Use **image generation** for a process diagram only when:

- The diagram is the **hero visual** of a presentation, poster, or cover — where aesthetic polish matters as much as content.
- The user wants a **stylized / illustrated** treatment beyond what Mermaid can produce.
- The diagram is **final** — won't be edited after publication.
- The user already tried Mermaid and wants something more designed.

If Mermaid clearly wins, **say so** and produce a Mermaid code block instead. The skill's role is helping the user get the right figure, not unnecessarily routing them to image generation.

## When you do proceed with image generation

The challenge is that process diagrams need **precise text in precise positions** with **correct connections**. Modern image models have improved at this, but errors compound: a misspelled node label is bad; a misspelled label plus a wrong arrow direction makes the figure unusable.

Strategy: **simplify ruthlessly**. An image-generated process diagram should have at most 6–8 nodes and clearly structured flow direction. For anything more complex, push back to Mermaid.

## Structural elements to capture

1. **Nodes** — the exact labels for each box / step. List them in order.
2. **Connections** — what connects to what, and what each arrow represents (sequence / feedback / data flow / dependency).
3. **Flow direction** — left-to-right, top-to-bottom, cyclical.
4. **Hierarchy** — are there levels, groupings, or is it a flat sequence?
5. **Style** — minimal flat / hand-drawn / isometric / corporate clean / academic schematic.
6. **Text density** — short labels (1–3 words per node) vs longer phrases. Short is much more reliable.

## Prompt skeleton — ChatGPT/OpenAI GPT Image

```
A clean [style] process diagram showing [process name].

LAYOUT:
- Overall flow direction: [left-to-right / top-to-bottom / circular]
- Number of stages/nodes: [N]
- Special structure: [linear / branching / cyclical-with-feedback]

NODES (render text exactly as quoted):
1. "[Node 1 label]" — [position, e.g. "left, large"]
2. "[Node 2 label]" — [position]
3. "[Node 3 label]" — [position]
4. "[Node 4 label]" — [position]
[etc.]

CONNECTIONS:
- Arrow from "[Node 1 label]" → "[Node 2 label]" labeled "[connection label]"
- Arrow from "[Node 2 label]" → "[Node 3 label]" labeled "[connection label]"
- Feedback arrow from "[Node 4]" → "[Node 1]" labeled "[connection label]"
[etc.]

VISUAL STYLE:
- [Node shape: rounded rectangles / circles / hexagons]
- [Color palette: monochrome / two-tone / categorical]
- [Line weight: thin / medium / bold]
- Clean, professional, geometric. No drop shadows. No decorative elements.

ASPECT RATIO: [ratio]
INTENDED USE: [where this will appear]
```

### Example — ChatGPT/OpenAI GPT Image prompt for "Monitoring–Restoration–Evaluation closed loop"

Brief: a closed-loop framework diagram for a report cover. Has 4 nodes with feedback arrows. The user has tried Mermaid and wants a more polished version for the cover.

```
A clean flat-design process diagram showing a closed-loop framework for ecological monitoring, restoration, and evaluation.

LAYOUT:
- Overall flow direction: circular (cyclical-with-feedback)
- Number of nodes: 4, arranged at the four cardinal points of a circle
- Center contains a small descriptive icon

NODES (render text exactly as quoted):
1. "Baseline & Monitoring" — top of circle, rounded rectangle
2. "Restoration Intervention" — right of circle, rounded rectangle
3. "Outcome Evaluation" — bottom of circle, rounded rectangle
4. "Adaptive Feedback" — left of circle, rounded rectangle

CONNECTIONS:
- Curved arrow from "Baseline & Monitoring" → "Restoration Intervention" (clockwise, top to right)
- Curved arrow from "Restoration Intervention" → "Outcome Evaluation" (clockwise, right to bottom)
- Curved arrow from "Outcome Evaluation" → "Adaptive Feedback" (clockwise, bottom to left)
- Curved arrow from "Adaptive Feedback" → "Baseline & Monitoring" (clockwise, left to top, closing the loop)
- Small inner double-headed arrows from each node toward the center icon, suggesting all four inform the central concept
- Center icon: small minimal river-and-fish silhouette, very simple, single color

VISUAL STYLE:
- Rounded rectangle nodes, medium-weight 2px stroke
- Color palette: deep teal nodes with cream interior, charcoal text, dark olive arrows
- Subtle off-white background, no gradient
- Clean geometric, modern academic poster aesthetic
- Avoid: drop shadows, glossy effects, decorative flourishes, 3D rendering

ASPECT RATIO: 1:1 square
INTENDED USE: hero diagram on the cover of an environmental research report
```

## Prompt skeleton — Gemini/Nano Banana

```
A [style] process diagram illustration. The diagram visualizes [process name] for [use context].

The structure is [structural description: cyclical / linear / branching]. [N] elements arranged [spatial layout].

Each element bears a label. Reading clockwise from the top: "[Node 1 label]", then "[Node 2 label]", then "[Node 3 label]", then "[Node 4 label]". [Continue for all nodes.]

Arrows connect [describe connections explicitly]. [Describe the visual character of the arrows].

[Visual style: shapes, colors, line weights, overall aesthetic]. [Negative space / background description].

Avoid [things that don't fit the aesthetic].

Aspect ratio: [ratio].
```

### Example — Gemini/Nano Banana prompt (same brief as above)

```
A clean flat-design process diagram illustration. The diagram visualizes a closed-loop framework for ecological monitoring, restoration, and evaluation, designed for the cover of an environmental research report.

The structure is cyclical: four labeled elements arranged at the four cardinal points of a circle, connected by curved arrows flowing clockwise. A small central icon anchors the composition.

Each element is a rounded rectangle bearing a label. Reading clockwise from the top: "Baseline & Monitoring" at twelve o'clock, "Restoration Intervention" at three o'clock, "Outcome Evaluation" at six o'clock, and "Adaptive Feedback" at nine o'clock.

Curved arrows connect each node to the next in clockwise order, completing the loop. A second set of small inner arrows links each node to the center, where a minimal silhouette of a river and a fish sits as the unifying concept.

The rounded rectangles are deep teal with cream interiors and charcoal text labels. The arrows are dark olive with medium-weight strokes. The background is soft off-white, no gradient. The overall aesthetic is clean, geometric, modern academic — the kind of diagram that would appear on the cover of a thoughtful research report.

Avoid drop shadows, glossy effects, decorative flourishes, 3D rendering, or any treatment that feels like generic corporate-PowerPoint clip art.

Aspect ratio: 1:1 square.
```

## Watch out for

- **More than 8 nodes**: error rate climbs sharply. Simplify or use Mermaid.
- **Arrow labels**: short labels work; sentences fail. If your arrows need explanatory text, the diagram is too complex for image generation — use Mermaid.
- **Hierarchical / nested diagrams**: image models struggle. Stick to flat structures (single-level circular, linear, or branching).
- **Equations or formulas on nodes**: don't. Image models hallucinate math.
- **Reading order**: in cyclical diagrams, the model sometimes places nodes in unexpected positions. Always state positions explicitly (twelve o'clock, three o'clock, etc.).

## Post-processing notes to surface

- **Every node label**: verify spelling character by character.
- **Arrow directions**: confirm they match the intended flow (this is the most common error).
- **Connections**: confirm every intended connection exists and no spurious ones were added.
- **For publication**: redo in Illustrator or rebuild in Mermaid. Image-generated process diagrams are usually for hero visuals or covers; for actual methods-section figures, Mermaid is more honest about being a diagram.
