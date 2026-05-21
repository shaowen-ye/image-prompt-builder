---
name: image-prompt-builder
description: Build ready-to-paste prompts or Markdown prompt sets for image-generation tools such as ChatGPT Images, OpenAI GPT Image models, Gemini image generation, and Nano Banana / Nano Banana Pro. Use when the user wants prompts for infographics, scientific illustrations, posters, covers, concept art, process diagrams, or multi-series figure packages to be rendered by an image model. Refuse and redirect requests requiring real-data charts, real geography, true network topology, precise numerical plots, or decision-critical visual accuracy; those need plotting, GIS, graph, or vector-diagram tools instead.
---

# Image Prompt Builder

## What this skill produces

For one figure or a multi-series figure package described by the user, produce either a Markdown response or a saved `.md` prompt file containing:

1. The **tool choice** (ChatGPT/OpenAI Images, Gemini/Nano Banana, or another image tool), captured or inferred up front
2. A **figure-type template selection** (infographic / scientific illustration / concept art / process diagram)
3. An **English prompt as a single copy-paste-ready code block**, written in the prompt style that the chosen tool responds best to
4. A **parallel Chinese version** of the prompt so the user can audit what is being requested
5. Recommended **generation parameters** (aspect ratio, quality/resolution when known, reasoning/thinking mode if the target tool exposes it, reference image attachments)
6. **Post-processing notes** — what to verify in the output (text, species morphology, numerical claims), and what to redo manually if the figure will appear in a formal report
7. For multi-series work, a **series-level style guide**, shared assumptions, and per-series prompt groups

Default to one prompt for one figure. When the user asks for multiple prompts, a prompt package, several series, campaign variations, or a deliverable `.md` file, switch to multi-series file mode.

## Operating modes

- **Fast mode** — use when the user asks for a quick prompt, gives a clear brief, or says to proceed. Infer low-risk missing details and list assumptions.
- **Rigorous mode** — use when the figure is for publication, has technical labels, uses references, or could trigger red-line issues. Ask only for missing details that materially change the prompt.
- **Single-figure mode** — default. Produce one figure prompt at a time.
- **Batch mode** — use when the user asks for several independent figure prompts in one response.
- **Multi-series file mode** — use when the user asks for multiple series, a prompt library, a campaign pack, a figure set, or delivery as a Markdown file. Build one `.md` file with all prompts, not just a long chat response.

## Hard red lines (refuse, redirect, never wrap into a prompt)

Before doing anything else, check whether the request falls into a category that AI image generation cannot handle safely for a formal deliverable. If any apply, refuse to generate the prompt and explain why:

- **Statistical charts based on real data** — bar charts, line charts, box plots, heatmaps with actual numbers. Image models may hallucinate axis values, bar heights, and data points even when labels look correct. → Redirect to R (ggplot2) or Python (matplotlib/seaborn).
- **Maps with real geography** — administrative boundaries, watercourses, station locations, real coordinates. Image models geographically hallucinate even when text is correct. → Redirect to QGIS / ArcGIS.
- **True network topologies** — food webs, ecological networks, social networks, citation graphs based on real interaction matrices. The topology is data-driven, not visual. → Redirect to cheddar / igraph / Gephi / Cytoscape.
- **Plots with specific numerical claims** — financial charts, hydrological time series, ecological metrics requiring exact values. → Same as above; use a plotting library.
- **Anything where the user will rely on visual accuracy of numbers, coordinates, or topology to make a decision.**

If the user pushes back ("just make it look approximately right"), still refuse for formal-deliverable contexts. Explain the failure mode (hallucinated data makes the deliverable indefensible under scrutiny). Offer the redirect.

Soft warning categories (proceed, but flag for post-verification):

- **Species morphology / anatomical illustrations** — image models can get fin counts, scale patterns, leaf venation subtly wrong. Generate, but tell the user to verify against a reference.
- **Habitat cross-sections / mechanism diagrams** — proportions and labeled features need expert review.
- **Anything with technical terminology in text** — even with strong text rendering, terms may misspell.

## Workflow

### Step 1 — Choose the tool

Ask the user which tool they will paste the prompt into when it materially affects the prompt. If the user has no preference, choose a default and state the assumption.

- **ChatGPT / OpenAI GPT Image** — default for structured composition, diagrams with short exact text, multi-panel layouts, and infographic-style hierarchy.
- **Gemini / Nano Banana / Nano Banana Pro** — default for photographic or cinematic scenes, multi-reference editing, iterative conversational edits, localized creative treatments, and image fusion.
- **Other tool** — adapt the prompt style to the tool's known strengths if the user names it.

If the user has no preference: "diagram-with-text / infographic" → ChatGPT/OpenAI GPT Image; "photographic / illustrative scene" → Gemini/Nano Banana; "edit an existing image iteratively" → Gemini/Nano Banana. If they say "whichever is better": default ChatGPT/OpenAI GPT Image for technical/structured figures, Gemini/Nano Banana for narrative/illustrative figures.

For tool-specific model names, parameter names, access tiers, and resolution limits, use current official documentation if the user needs API-ready instructions. Do not hard-code release dates, architecture claims, exact accuracy percentages, or model IDs unless verified during the task.

### Step 2 — Capture the figure brief

In rigorous mode, ask in a single batch (use a structured selector if available):

- **Figure type** — infographic / scientific illustration / concept art / process diagram / cover art / poster / other
- **Use context** — academic paper figure / report figure / presentation slide / poster / cover / social media
- **Text in image** — must contain specific text (provide the exact text) / minimal text (axis labels only) / no text / placeholder only (filled later by hand)
- **Aspect ratio / size** — 16:9 / 4:3 / 1:1 / 2:3 / 3:2 / specific dimensions
- **Style direction** — flat infographic / isometric / photorealistic / watercolor / line drawing / cross-section diagram style / etc.
- **Reference materials** — does the user have a reference image, sketch, or prior figure to attach? (Critical for Nano Banana multi-reference workflows.)

For multi-series file mode, also capture or infer:

- **Project / package name** — used for the file title and filename
- **Series count and names** — e.g. cover concepts, infographic variants, scientific illustration set, social media adaptations
- **Prompts per series** — default 3 prompts per series unless the user specifies a count
- **Shared visual identity** — palette, typography direction, composition density, audience, forbidden elements
- **Variation axis per series** — what changes between prompts: composition, mood, viewpoint, medium, audience, aspect ratio, or callout strategy

In fast mode, infer missing details from the brief:

- Aspect ratio: 16:9 for slides/report figures, 1:1 for square social/cover concepts, 4:5 or 2:3 for portrait covers/posters.
- Text strategy: if the user did not provide exact text, generate placeholder-free imagery or numbered markers rather than inventing labels.
- Style: use a conservative professional style matching the use context.
- Multi-series defaults: 3 series × 3 prompts, one shared style guide, 16:9 for report/slide figures unless the use context suggests otherwise.

Don't ask all separately. Bundle into 1–3 compact questions only when needed.

### Step 3 — Run the red-line check (mandatory)

After capturing the brief, before writing the prompt, run the red-line check above. In multi-series file mode, run it once at the package level and again for any series that might involve data, maps, topology, or exact numbers. If anything triggers, refuse or split the package: redirect unsafe figures to plotting/GIS/graph/vector workflows and continue only with safe image-generation prompts.

If the request falls in a soft-warning category, note it; you'll surface it in post-processing notes.

### Step 4 — Load the relevant template

Pick exactly one based on figure type:

- **Infographic / poster / cover with structured text** → `references/template-infographic.md`
- **Scientific illustration (habitat cross-section, life cycle, mechanism diagram)** → `references/template-scientific-illustration.md`
- **Concept art / style exploration** → `references/template-concept-art.md`
- **Process diagram / flowchart-like** → `references/template-process-diagram.md` (this template starts with a "consider Mermaid instead" decision)

If the request crosses categories, pick the dominant one and borrow phrasing patterns from the secondary.

Always read `references/methodology.md` on first use in a session — it contains the ChatGPT/OpenAI Images vs Gemini/Nano Banana style differences, the iteration patterns, and the common pitfalls.

For reference figures grounded in the user's prior project context (ecology, river systems, etc.), read `references/examples.md` for worked examples.

### Step 5 — Write the prompt

Follow the template's structure for the chosen tool. Hard rules:

- **English first, complete and standalone.** The English prompt is the canonical version the user will paste.
- **Chinese parallel version directly after**, presented as a separate code block clearly labeled. The Chinese version is for the user to audit content, not for pasting (image models respond better to English for most styles, even when CJK text is rendered inside the image).
- **No bilingual mash-up inside one prompt.** Two separate code blocks, both complete.
- **For text-inside-the-image**: quote the exact text both versions need to render, in the language the user wants displayed.
- **Recommend parameters explicitly**: aspect ratio, quality/resolution when known, whether to enable reasoning/thinking mode if the chosen tool exposes it, and whether to attach reference images.
- **Append post-processing notes**: what to verify (text spelling, morphology, color accuracy), and whether the output should be redrawn in Illustrator/Affinity for formal publication.
- **For multi-series packages**: write a concise shared style guide first, then make each prompt standalone. A user should be able to copy any single English prompt without reading the rest of the file.
- **Avoid near-duplicates**: each prompt in a series must vary along a named axis, not just swap adjectives.

### Step 6 — Deliver

For a single figure or short batch, output in the response:

````
## Image prompt for: <brief figure name>

**Tool**: <ChatGPT/OpenAI GPT Image / Gemini Nano Banana / other>
**Recommended parameters**: <aspect ratio>, <quality/resolution if known>, <thinking/reasoning mode if available>, <reference images>

### English prompt (paste into <tool>)
```
[full English prompt]
```

### Chinese parallel version (for your audit, not for pasting)
```
[full Chinese prompt]
```

### Post-processing notes
- Verify: <list>
- Redo manually if: <list>
- For formal publication: <recommendation>
````

If the user wants more than one figure, repeat the structure for each — but produce them one at a time unless the user explicitly batches them.

For multi-series file mode, build a single Markdown file with this structure:

````
# <Project name> — Image Prompt Set

> Tool target, intended use, maintainer/date if known

## 0. Usage notes
[How to use the prompts, which block to paste, what to attach, what to verify]

## 1. Shared assumptions and visual identity
[Tool choice, aspect ratios, palette, typography direction, reference image handling, red-line status]

## Series A: <series name>
> Series goal: <one sentence>
> Variation axis: <composition / mood / viewpoint / medium / etc.>

### Prompt A1: <name>
**Tool**: <tool>
**Recommended parameters**: <parameters>

#### English prompt
```
[standalone English prompt]
```

#### Chinese parallel version
```
[complete Chinese audit version]
```

#### Post-processing notes
- Verify: <list>
- Manual edits: <list>

### Prompt A2: <name>
...

## Series B: <series name>
...

## Appendix: Red-line and QA checklist
[What was refused/redirected if any; final checks before using the images]
````

Output location rules:

1. If the user specifies a path, save there.
2. Else save in the current working directory when file writing is available.
3. Else return the Markdown inline.

Filename rules: use `<project-slug>_image_prompts.md`; make the slug lowercase ASCII with hyphens where practical. For Chinese-only titles, use a short pinyin/English slug or `image-prompts-YYYYMMDD`. If the target filename exists, append `-v2`, `-v3`, etc. Do not overwrite without user confirmation.

After saving, report the saved path and a brief count: number of series, number of prompts, and any refused/redirected items.

### Step 7 — Offer iteration

After delivery, briefly offer:

- "Run it once and paste the result here — I can iterate on the prompt."
- "If you want a different style, I can rewrite without re-capturing the brief."

Don't push. The user iterates at their own pace.

## Quality gate before delivering

Before presenting, perform a quick explicit self-check and fix failures:

- Tool choice is explicit and matches the user's intent or stated assumptions.
- Red-line check was run and passed, or the request was refused and redirected.
- English prompt is one self-contained code block.
- Chinese parallel version is a separate code block, complete and equivalent.
- Text-in-image is quoted exactly in the language to be rendered.
- Aspect ratio and available tool parameters are recommended without inventing unsupported settings.
- Post-processing notes name what to verify.
- If a soft-warning category triggered, the warning appears in post-processing notes.
- If fast mode inferred missing details, assumptions are listed.
- For multi-series files, every prompt is independently copy-pasteable, series variation axes are explicit, and the saved Markdown path is reported.

## What this skill does NOT do

- Generate the image itself unless the active runtime provides an image-generation tool and the user explicitly asks to generate rather than build a prompt.
- Produce data charts, real maps, or true network topologies — those require code or GIS, not image models.
- Replace Mermaid/draw.io for editable concept diagrams — for flowcharts the user will keep editing, suggest Mermaid first (the process-diagram template does this).
- Build real charts/maps/topologies inside an image prompt package; redirect those items to the right workflow and include the redirect in the Markdown file if helpful.

Keep boundaries clean. If the user wants a code-based plot or a Mermaid concept diagram, hand off to those workflows instead.
