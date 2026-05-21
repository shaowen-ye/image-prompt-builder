# Template — Infographic / Poster / Cover

Use this template when the figure is an **information-dense visual where text is central**: infographics, conference posters, journal cover candidates, presentation slide hero images, social media campaign visuals.

This is the figure type where ChatGPT/OpenAI image models often have an advantage because of structured layout and text-aware prompt following. Gemini/Nano Banana can also work well, especially when reference images, brand style, or iterative editing matter.

## Contents

- Structural elements to capture
- Prompt skeleton — ChatGPT/OpenAI GPT Image
- Prompt skeleton — Gemini/Nano Banana
- Watch out for
- Post-processing notes

## Structural elements to capture from the user

Before writing the prompt, the user should give you:

1. **Title and key text** — the actual words to appear, in the language they should appear in. Quote it exactly.
2. **Visual hierarchy** — what's the largest element, what's secondary, what's tertiary.
3. **Data hierarchy if applicable** — for an infographic, what numbers or labels need to appear (and these must be either real, user-provided, or explicitly placeholder).
4. **Style direction** — flat 2D / isometric 3D / editorial illustration / minimal modernist / scientific journal plate / brand-style consistent.
5. **Color palette** — named (viridis, ColorBrewer Set2, monochrome blue, brand colors) or hex codes.
6. **Aspect ratio** — poster (typically 2:3 or 3:4), cover (1:1 or magazine 4:5), slide (16:9), social (1:1 or 4:5).

## Prompt skeleton — ChatGPT/OpenAI GPT Image

```
A [style direction] [figure type] designed for [use context].

LAYOUT:
- [Top region]: [what appears there]
- [Middle region]: [what appears there]
- [Bottom region]: [what appears there]

TEXT (render exactly as quoted):
- Title: "[exact title text]"
- [Other text element]: "[exact text]"
- [Footer / source]: "[exact text]"

VISUAL ELEMENTS:
- [Element 1] in [position], [color/size]
- [Element 2] in [position], [color/size]
- [Element 3] in [position], [color/size]

STYLE CONSTRAINTS:
- [color palette]
- [typography hint, e.g. "serif headlines, sans-serif body"]
- Clean, professional, [adjective].
- Avoid: clip art, stock photography, decorative gradients, drop shadows, generic AI-art aesthetics.

ASPECT RATIO: [ratio, e.g. 3:4 portrait, 16:9 landscape]
INTENDED USE: [where this will appear]
```

### Example — ChatGPT/OpenAI GPT Image infographic prompt

For a journal cover candidate on "Reservoir cyanobacteria bloom forecasting":

```
A flat editorial scientific illustration designed for an academic journal cover.

LAYOUT:
- Top third: a stylized reservoir surface seen from above, with a partial bloom forming a teal-green swirl pattern.
- Middle third: a clean horizontal band containing the title and subtitle.
- Bottom third: three small icon panels representing monitoring, forecasting, and management — each in muted teal-and-charcoal.

TEXT (render exactly as quoted):
- Main title: "Forecasting Cyanobacterial Blooms"
- Subtitle: "A Methods Review"
- Bottom-right corner small text: "Research Theme"

VISUAL ELEMENTS:
- Reservoir swirl: organic, painted look, teal and pale yellow-green, NOT photorealistic
- Three icon panels (left to right): a satellite, a graph with predictive line, a regulatory gate; all in the same line-illustration style, monochrome charcoal on cream
- Subtle texture suggesting hand-mixed inks, NOT digital gradient

STYLE CONSTRAINTS:
- Color palette: deep teal (#0F4C5C), bloom green (#7FB069), warm cream (#FDF6E3), charcoal (#2D3436)
- Typography hint: serif for the title, sans-serif for the subtitle and footer
- Mid-century scientific journal aesthetic, restrained, confident
- Avoid: clip art, stock photography, glowing effects, photorealistic water, generic AI-art aesthetics

ASPECT RATIO: 4:5 portrait (suitable for academic journal cover)
INTENDED USE: cover candidate for a special issue of a freshwater science journal
```

## Prompt skeleton — Gemini/Nano Banana

```
An [editorial / scientific / commercial] illustration in the style of [reference style]. The image is designed as a [figure type] for [use context].

The composition shows [scene description as a narrative]. [Spatial description of how elements relate].

[Text element description]: the words "[exact text]" appear [where, in what typography hint].

[Style and palette description as visual language, not as constraints]. Light falls [direction], the mood is [adjective]. The medium feels like [print medium reference].

Avoid [specific things to avoid, framed positively where possible].

Aspect ratio: [ratio].
```

### Example — Gemini/Nano Banana infographic prompt (same brief as above)

```
An editorial scientific illustration in the style of a mid-century natural science journal cover, designed for an academic journal special-issue cover.

The composition divides cleanly into three horizontal bands. The top band shows a reservoir surface seen from above, with a partial cyanobacterial bloom forming an organic teal-green swirl pattern across the water — painted in a hand-mixed-ink aesthetic rather than photorealistic. The middle band is a clean cream-colored strip carrying the title typography. The bottom band contains three small monochrome line-illustration icons arranged left to right: a satellite, a graph with a clearly drawn predictive line trending upward, and a regulatory water gate.

The title "Forecasting Cyanobacterial Blooms" appears in a confident serif, with the subtitle "A Methods Review" in a smaller sans-serif directly beneath. A small footer reads "Research Theme" in the bottom-right corner.

The palette is restrained: deep teal water, soft bloom green, warm cream background, charcoal line work. Light is even and overhead, suggestive of natural daylight on a printed page. The texture feels like high-quality printing on uncoated paper, with subtle ink variation.

Avoid digital glow, photorealistic water, glossy gradients, drop shadows, decorative flourishes, or any generic AI-illustration aesthetic.

Aspect ratio: 4:5 portrait.
```

## Watch out for

- **Long text passages**: both models handle a few short phrases well. For a body paragraph, generate without it and add text in post.
- **Specific numerical claims** in an "infographic" → red-line territory. If the user wants real numbers, the figure should be a real chart (R/Python), not an image-model output.
- **Multi-language text in one image**: works in both models for short labels, but verify each language separately.
- **Brand-specific fonts**: image models approximate fonts. Don't expect exact typography match — for brand work, generate the layout with the image model and overlay real font in Illustrator.

## Post-processing notes to surface

- Text spelling — every character.
- Numerical claims — if any appear, verify they match the source data.
- Color hex codes — image models approximate; if exact branded color matters, swap in post.
- Composition — if the figure will be printed, check the safe-margin/bleed implications of the aspect ratio.
