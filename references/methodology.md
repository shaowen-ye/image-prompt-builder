# Methodology — image prompt design for ChatGPT/OpenAI Images and Gemini/Nano Banana

This file is the playbook. Read it on first use in a session. It contains the prompt-style differences between the two main tools, iteration patterns, and the pitfalls that show up over and over.

## Contents

- 1. Tool prompt styles
- 2. Iteration loop
- 3. Common pitfalls
- 4. When not to use image generation
- 5. Chinese parallel version
- 6. Multi-series prompt files
- 7. Post-processing verification

## 1. The two tools have meaningfully different prompt styles

This is the single most important fact. A prompt that works well in ChatGPT/OpenAI Images often produces mediocre results in Gemini/Nano Banana, and vice versa. Match the prompt to the tool and verify current model names/parameters if the user needs API-ready instructions.

### ChatGPT / OpenAI GPT Image

Current OpenAI image models are strong for structured composition, text-aware layouts, image generation, and editing. Model IDs, quality settings, supported sizes, and API surfaces change over time; check the official OpenAI image-generation docs before giving API-ready model names or parameters.

**Prompt style that works**:

- Structured order: **background/scene → subject → key details → constraints → intended use**.
- State the use case explicitly ("an infographic for a research presentation", "a UI mockup for a B2B SaaS dashboard"). The model uses this to set polish level.
- For text-in-image: quote the exact text in double quotes. The model honors quoted text reliably.
- For layout: name the regions ("top half / bottom half", "left panel / right panel", "centered headline, three columns below").
- Negative constraints work: "Avoid clip art, stock photography, gradients, shadows, decorative elements, or anything that feels generic or overdesigned."
- For multi-panel consistency: request all panels in one prompt with a shared style description. If the target tool exposes a reasoning or high-quality mode, recommend it only after verifying it exists.

**Parameters**:
- Use the current official docs for model ID, endpoint, supported sizes/aspect ratios, quality values, output formats, and image-editing input limits.
- For formal deliverables, recommend the highest practical quality/resolution setting the tool supports.
- For API prompts, distinguish Image API / image-generation endpoint behavior from conversational image tools when relevant.

**Watch out for**:
- Text rendering, layout placement, and brand consistency are improved but still need verification.
- Reference-image editing may have different cost, quality, or fidelity settings from text-to-image generation.
- Structured layouts can still drift; keep prompt regions explicit.

### Gemini / Nano Banana / Nano Banana Pro

Gemini image generation is strong for conversational image creation/editing, reference-image workflows, photographic or cinematic scenes, multilingual text attempts, and iterative changes. Model names, access tiers, resolution limits, and grounding behavior change over time; check the official Gemini image-generation docs before giving API-ready model names or parameters.

**Prompt style that works**:

- Narrative / cinematic / photographic description. The model responds to language of light, lens, composition, atmosphere.
- Subject and scene as a story rather than a layout brief.
- For text-in-image: state it inline naturally, in quotes. Keep text short for reliability; long passages should usually be added in post.
- For style: name the medium and reference style ("editorial illustration in the style of mid-century scientific journal plates", "isometric 3D cartoon with PBR materials and soft lighting").
- Multi-reference: when feeding logos / style guides / prior figures, name what each reference contributes.
- Multi-turn edits: write the initial prompt for a base image, then iterate with "change X, keep Y" follow-ups.

**Parameters**:
- Use current official docs for model names, access tiers, resolution, aspect ratios, watermarking, safety requirements, and reference-image limits.
- If the user has Pro access and the tool exposes a reasoning/thinking option, recommend it for complex layouts, strict text placement, and multi-frame consistency.

**Watch out for**:
- The model may misinterpret information or produce factually incorrect results when generating infographics, annotated diagrams, or representing complex data. **Always verify data-driven outputs.**
- Small faces and accurate spelling still fail occasionally.
- Lighting transitions (day to night), masked editing, multi-image blending sometimes produce artifacts.

### Side-by-side: same figure, two prompt styles

For a "river habitat cross-section showing pool-riffle sequence with substrate and flow":

| Aspect | ChatGPT/OpenAI Images phrasing | Gemini/Nano Banana phrasing |
|---|---|---|
| Opening | "A flat, professional scientific cross-section illustration of a mountain river habitat." | "An editorial illustration in the style of a mid-century natural science journal plate, depicting a mountain stream cross-section." |
| Layout | "Left side: deep pool with slower flow indicated by horizontal arrows. Right side: shallow riffle with turbulent flow and cobble-boulder substrate." | "Light falls from the upper left, revealing a deep pool on one side that flows naturally into a shallow riffle, with cobbles catching highlights." |
| Constraints | "Pure white background, no decorative elements, no gradients, flat color blocks with thin black outlines." | "Painted with limited palette — warm sand, cool blue water, dark substrate. Crisp lines, no atmospheric perspective." |
| Text instruction | "Leave blank placeholder boxes where labels will appear; do not render any text." | "Show the scene without any labels — clean and uncluttered." |

Both produce a usable scientific illustration. The phrasing is different because the models reward different signals.

## 2. The iteration loop

Image prompts almost never land on the first try. The loop:

1. **Generate** with the initial prompt.
2. **Diagnose** what's wrong. Don't just say "make it better" — name the specific failure: "text is misspelled", "the proportions of element X are off", "the color palette has unwanted warm bias", "the composition is too centered".
3. **Adjust the prompt** with a targeted change, not a rewrite. Add a sentence addressing the specific failure; remove conflicting instructions.
4. **Regenerate**.

For Gemini/Nano Banana, prefer **conversational edits** ("keep everything else, but change the substrate color to lighter gray, and remove the small fish in the upper right") over full prompt rewrites when using a tool that preserves conversational image context.

For ChatGPT/OpenAI Images, multi-turn editing may work in the product UI or Responses-style workflows, but rewriting the prompt with the targeted change is also fine.

Diminishing returns set in around iteration 5. If you're not converging by then, the prompt structure is wrong — re-read the template and start fresh.

## 3. Common pitfalls

| Pitfall | Symptom | Fix |
|---|---|---|
| Stuffing 20 elements into one prompt | Mushy, generic output | Cut to 5–7 key elements; mention secondary elements only as "environment" |
| Asking for "accurate" technical content | Plausible-looking but subtly wrong | Generate the visual shell; verify factual content separately; redraw critical labels in vector tool |
| Mixing styles ("photorealistic but flat illustration") | Confused, off-style output | Pick one style and commit |
| Not specifying use case | Generic "AI art" feel | Always state the intended use ("for a peer-reviewed journal", "for a conference poster") |
| Requesting numerical accuracy | Wrong numbers in the figure | Generate without numbers; type real numbers over in post |
| Asking for "many" of something | Inconsistent count, bad composition | Specify exact count: "show exactly 4 fish, not 3 or 5" |
| Vague color direction | Default warm bias (especially Nano Banana) | Name colors explicitly with hex codes if possible, or named palettes ("ColorBrewer Set2", "viridis") |
| Negative-only constraints | Model ignores prohibitions | Pair every "no X" with a positive "instead use Y" |

## 4. When NOT to use image generation at all

Even as image models improve, several categories are still better served by other tools. The skill's red-line check handles these, but as background:

- **Real-data charts** → R/Python. Even if the model can render axis labels, the data values themselves will be wrong.
- **Maps with real geography** → QGIS. Coastlines, rivers, administrative boundaries get hallucinated.
- **Network topologies (food webs, citation graphs, social networks)** → cheddar / igraph / Gephi / Cytoscape. The topology is the data; visual generation can't recover it.
- **Editable concept diagrams that will keep evolving** → Mermaid / draw.io. Vector, version-controllable, editable forever.
- **Equations and chemical structures** → LaTeX / ChemDraw. Image models render plausible-looking equations that are mathematically wrong.

## 5. The Chinese parallel version

The skill outputs an English prompt as the canonical version to paste, and a Chinese version in a separate code block for the user to audit. Two notes:

- The Chinese version is a **direct translation of the English prompt's content**, not a separately-tuned prompt. The goal is auditability ("does the English prompt actually say what I want?"), not bilingual paste-and-pick.
- Image-rendered text inside the figure follows the language the user specified. If the user wants Chinese text inside the image, both the English and Chinese prompt versions quote the same Chinese text — and the user pastes the English version (which contains the quoted Chinese characters).

Modern image models can render CJK text much better than earlier generations, but text still needs character-by-character verification. English-language instructions with quoted CJK text-in-image is usually the most reliable pattern.

## 6. Multi-series prompt files

When the user asks for multiple series, do not produce a loose pile of prompts. Build a coherent prompt set:

1. **Shared visual identity first** — tool target, audience, palette, typography direction, level of detail, reference-image policy, and forbidden elements.
2. **Series goals second** — each series needs a one-sentence purpose and a named variation axis.
3. **Standalone prompts third** — every English prompt must be copy-pasteable without reading the rest of the file.
4. **Chinese audit versions fourth** — every prompt gets a complete Chinese parallel version, not a summary.
5. **QA notes last** — repeat post-processing risks where they differ by series.

Good variation axes:

- Composition: centered hero / split scene / grid / close-up / wide scene
- Mood: formal / editorial / cinematic / warm / austere
- Medium: flat vector / scientific plate / watercolor / isometric / photographic
- Audience: academic / executive / public outreach / social media
- Detail density: sparse cover visual / medium-density explainer / dense infographic shell
- Viewpoint: cross-section / top-down / oblique / macro / field scene

Bad variation axes:

- Swapping synonyms while keeping the same composition
- Changing only colors with no conceptual difference
- Adding more elements to every later prompt until the series becomes cluttered
- Mixing incompatible styles inside one series

For prompt-set files, include a red-line note. If a requested series is unsafe for image generation (real maps, data plots, true topologies), either remove it from the image prompt set or include it as a redirected item with the correct tool recommendation.

## 7. Post-processing — what to verify

Every figure that will appear in a formal deliverable needs post-verification:

- **Text**: spelling, terminology, numerical values. Even high text accuracy still leaves visible errors in dense infographics.
- **Morphology**: species anatomy, anatomical structures, chemical groupings. Image models pattern-match on visual similarity, not on correctness.
- **Proportions**: cross-sections, comparative sizes, scale indicators.
- **Color semantics**: if colors carry meaning (e.g. "blue for water", "red for warning"), confirm the model didn't invert them.

For top-tier publication, generate the visual shell with the image model, then redraw critical elements in Illustrator / Affinity / Inkscape. The image model gives you the composition and aesthetic in 30 seconds; the manual redraw gives you the correctness in the next 30 minutes.
