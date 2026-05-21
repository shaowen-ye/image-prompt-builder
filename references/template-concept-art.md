# Template — Concept Art / Style Exploration

Use this template when the user wants **visual exploration**, not a finished deliverable: mood boards, style direction sketches, "what could this look like" experiments, branding concept variations, atmosphere studies.

The defining feature: the user is exploring possibilities, not producing the final figure. Constraints are looser. Iteration is expected.

## Contents

- When to use this template vs others
- Structural elements to capture
- Prompt skeleton — ChatGPT/OpenAI GPT Image
- Prompt skeleton — Gemini/Nano Banana
- Watch out for
- Post-processing notes

## When to use this template vs others

- Use **concept art template** when the user says "show me what this could look like", "I'm exploring styles", "give me some directions for a poster I'll later commission".
- Use **infographic template** when the user has a specific deliverable in mind with text and data hierarchy.
- Use **scientific illustration template** when morphological accuracy matters.

For concept art, the focus shifts from "render exactly this" to "evoke this mood / explore this style".

## Structural elements to capture

1. **Concept / subject** — what the image is exploring (a place, a mood, a brand direction, a metaphor).
2. **Mood / atmosphere** — words like "contemplative", "energetic", "austere", "warm and inviting", "stark and clinical".
3. **Style reference** — naming a style or referencing artists/movements is OK in concept art (whereas in scientific illustration it's risky).
4. **Number of variations** — concept art often benefits from 3–4 variations on a theme.
5. **What's flexible vs fixed** — the user should declare what they're firm on (e.g. "must be in cool colors", "must include a river") and what's open ("anything else, surprise me").

## Prompt skeleton — ChatGPT/OpenAI GPT Image

```
A [style reference] concept illustration exploring [concept / subject].

MOOD: [mood adjectives, atmosphere words]

VISUAL DIRECTION:
- [Element 1 with creative latitude]
- [Element 2 with creative latitude]
- [What feels right vs what to avoid]

FIXED CONSTRAINTS (must include):
- [Hard requirement 1]
- [Hard requirement 2]

FLEXIBLE (surprise me):
- [Aspect open to creative interpretation]

STYLE:
- [Reference to style movement or artist if appropriate]
- [Medium reference: oil, ink wash, digital, gouache, etc.]

ASPECT RATIO: [ratio]
PURPOSE: concept exploration, not final deliverable
```

For multiple variations, request explicitly: "Generate four variations on this concept, each with a different [varying dimension, e.g. color palette / composition / time of day]." Recommend a reasoning/high-quality mode only if the target tool exposes one.

### Example — ChatGPT/OpenAI GPT Image concept art prompt

Brief: explore visual direction for an environmental research annual report cover. Concept: "patient, attentive field observation". Open style.

```
A concept illustration exploring the theme of patient, attentive freshwater research.

MOOD: contemplative, quietly observant, scientifically curious, neither flashy nor cold

VISUAL DIRECTION:
- A single figure (silhouette or hint of person) engaged in field observation by a river — taking a sample, recording notes, or watching the water
- Natural environment with hints of instrumentation (small sensors, marked stakes) integrated without being obtrusive
- Water as a present, central element — texture, surface, depth implied

FIXED CONSTRAINTS (must include):
- A river or stream as a clear element
- A human presence (subtle, not heroic)
- A sense of measurement / attention / care

FLEXIBLE (surprise me):
- Time of day, weather, season
- Whether the human is foreground, midground, or background
- Realism level — could be impressionistic or precise

STYLE:
- Reference: contemporary editorial magazine illustration — confident draftsmanship, restrained palette, intelligent composition
- Medium reference: gouache or digital painting with brush-mark texture
- Avoid: photorealistic stock imagery, scientific clinical aesthetic, corporate slick illustration

ASPECT RATIO: 4:5 portrait (annual report cover)
PURPOSE: concept exploration to choose a visual direction; not the final cover
```

## Prompt skeleton — Gemini/Nano Banana

Gemini/Nano Banana especially rewards narrative concept prompts. The skeleton:

```
[Style reference / medium] illustration. The mood is [mood], the atmosphere [adjectives]. The image is a concept exploration for [purpose].

[Describe the scene as a story or a moment]. [Walk through what one sees, evoking the feeling].

The light is [direction, quality]. The palette feels [color description as feeling]. The medium suggests [print or paint medium].

[What must be present, framed positively]. [What feels wrong for this concept, framed as "rather than"].

Aspect ratio: [ratio]. Generate [N] variations.
```

### Example — Gemini/Nano Banana concept art prompt (same brief)

```
An editorial illustration in the style of contemporary magazine visual essays. The mood is contemplative, quietly observant, scientifically curious. The atmosphere is patient — neither flashy nor cold. The image is a concept exploration for the cover of an environmental research annual report.

The scene shows a single human figure engaged with a river — perhaps crouched on a bank taking a water sample, perhaps standing in shallow water with a sensor, perhaps half-silhouetted against the morning light. The river is a present, central element: visible texture on its surface, a sense of depth beneath. Small hints of scientific work are woven in — a marked measurement stake, a notebook, a sensor lead disappearing into the water — but the human's attention to the water, not the instruments, is the subject.

Light is soft and directional, suggesting early morning or late afternoon. The palette feels muted and considered: cool water tones, warm earth on the banks, a single warm accent on the human figure. The medium suggests gouache or digital painting with visible brush-mark texture and confident draftsmanship.

The scene must include a river or stream as a clear element, a human presence treated with restraint rather than heroism, and a sense of measurement, attention, and care.

Rather than photorealism, stock imagery, sterile clinical aesthetic, or corporate slick illustration — the image should feel like a thoughtful editorial commission.

Aspect ratio: 4:5 portrait. Generate 4 variations exploring different times of day, compositions, and the figure's relationship to the water.
```

## Watch out for

- **Style references to specific living artists**: avoid. Use movements, publications, or genres instead.
- **Variations**: if the chosen tool supports multi-image variation generation or a reasoning/high-quality mode, use it. Otherwise regenerate and curate manually.
- **Over-constraining**: concept art benefits from leaving room. If the prompt has 15 hard constraints, you're not exploring — you're refining a fixed brief. Use the infographic or scientific illustration templates instead.
- **Knowing when to stop**: once you have a direction you like, switch to the appropriate template (infographic / scientific illustration) to produce the final figure with tighter constraints. Don't keep iterating in concept mode.

## Post-processing notes to surface

- Concept art usually isn't post-processed — it's a step before the final commission.
- If a concept piece is going to be used as-is (e.g. some annual reports use directly-generated covers), apply the standard post-processing: verify all text, check for inadvertent text artifacts, redraw critical elements in vector if going to print.
- Keep the prompt that produced the favored variation — it becomes the seed for the final brief.
