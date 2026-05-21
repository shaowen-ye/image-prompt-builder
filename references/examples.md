# Worked examples — image prompt builder

Three generic worked examples showing the intended flow: brief capture -> red-line check -> template selection -> prompt delivery. The first two are positive examples; the third is a negative example showing how the skill should refuse and redirect.

## Contents

- Example 1 — Habitat cross-section illustration
- Example 2 — Ecosystem services concept diagram
- Example 3 — Refused real watershed map
- Example 4 — Multi-series prompt-set Markdown file

---

## Example 1 — Habitat cross-section illustration

### Brief captured

- **Figure**: river habitat longitudinal cross-section showing pool-riffle sequence, substrate gradient, and flow regime
- **Use context**: methods-section figure in an environmental research report
- **Tool chosen**: ChatGPT/OpenAI GPT Image, because the user wants structured composition with clean marker placement
- **Text in image**: numbered marker circles only; no text labels in image
- **Aspect ratio**: 16:9 landscape
- **Style**: flat 2D scientific illustration, natural-science journal plate aesthetic
- **Reference materials**: none

### Red-line check

- Real-data chart? No — conceptual / typical-case illustration.
- Real geographic map? No — generic habitat, not a specific river segment.
- True network topology? No.
- Specific numerical claims? No.
- Proceed. Soft warning: morphology and substrate proportions need post-verification.

### Template chosen

`template-scientific-illustration.md`.

### Delivery

````
## Image prompt for: River habitat pool-riffle cross-section

**Tool**: ChatGPT/OpenAI GPT Image
**Recommended parameters**:
- Aspect ratio: 16:9 landscape
- Quality/resolution: highest practical setting available
- Reasoning/thinking mode: enable only if the target tool exposes it
- Reference images: none needed

### English prompt (paste into ChatGPT/OpenAI image tool)
```
A flat 2D scientific illustration depicting a mountain stream habitat showing a pool-to-riffle transition, viewed as a longitudinal cross-section: a side view through the water column.

COMPOSITION:
- Left third: deep pool with calm layered water surface, fine sediment and silt on the bed.
- Middle third: transitional zone where the water shallows, surface develops gentle ripples, and substrate shifts from sand to small gravel.
- Right third: shallow riffle with turbulent broken-water surface and a bed of angular cobbles and boulders.

KEY FEATURES:
- Subtle horizontal arrows in the water column indicate left-to-right downstream flow.
- Substrate gradient is visually clear: fine and rounded on the left, coarse and angular on the right.
- Water surface is smooth in the pool and broken white in the riffle.
- Show a few small generic fish silhouettes: two in the pool depth, one in the transition zone, none in the turbulent riffle.
- Add a simple hint of riparian vegetation along the top edge.
- No people, no buildings, no site-specific landmarks.

LABELS:
- Show numbered label markers (1), (2), (3), (4), (5) as small black-outlined white circles at: (1) pool surface, (2) pool substrate, (3) transitional zone, (4) riffle substrate, (5) riffle water surface.
- Do not render any label text; labels will be added manually later.

STYLE:
- Muted teal-blue water, warm sand substrate, gray-brown rocks, soft sage vegetation.
- Clean line work, flat educational illustration, subtle print texture.
- Natural-science journal plate aesthetic: restrained, precise, not decorative.
- Avoid photorealistic water reflections, glowing effects, atmospheric blur, drop shadows, glossy 3D, or generic stock-illustration styling.

ASPECT RATIO: 16:9 landscape.
INTENDED USE: methods-section figure in an environmental research report.
```

### Chinese parallel version (for audit, not for pasting)
```
一张平面 2D 科学插图,描绘山区溪流生境中从深潭到浅滩的过渡,以纵向剖面呈现:侧视、穿过水柱的剖面图。

构图:
- 左三分之一:深潭,水面平静分层,河床为细泥沙和细沉积物。
- 中三分之一:过渡区,水体变浅,水面出现轻微涟漪,底质由砂逐渐过渡到小砾石。
- 右三分之一:浅滩,水面湍流破碎,河床为棱角分明的卵石和漂砾。

关键特征:
- 水柱中用微弱的水平箭头表示从左到右的下游流向。
- 底质梯度清晰:左侧细而圆,右侧粗而有棱角。
- 深潭水面平滑,浅滩水面呈白色破浪。
- 显示几条小型通用鱼类剪影:深潭 2 条,过渡区 1 条,湍流浅滩 0 条。
- 顶部边缘加入简单的河岸植被暗示。
- 无人物、无建筑、无特定地点标志物。

标签:
- 在以下位置显示编号标记圆圈 (1)、(2)、(3)、(4)、(5),为黑色描边白色小圆:(1) 深潭水面,(2) 深潭底质,(3) 过渡区,(4) 浅滩底质,(5) 浅滩水面。
- 不渲染任何标签文字;标签之后手动添加。

风格:
- 柔和青蓝色水体、暖砂色底质、灰棕色岩石、柔和鼠尾草绿色植被。
- 线条干净、平面教育插图、轻微印刷纹理。
- 自然科学期刊图版美学:克制、准确、不装饰化。
- 避免照片级水面反射、发光效果、大气模糊、投影、光滑 3D 或通用图库插画风格。

宽高比:16:9 横向。
预期用途:环境研究报告的方法章节插图。
```

### Post-processing notes
- Verify marker count and positions.
- Verify flow arrows point left to right.
- Verify substrate gradient is fine-to-coarse from left to right.
- Add final labels manually in a vector editor.
````

---

## Example 2 — Ecosystem services concept diagram

### Brief captured

- **Figure**: concept diagram showing four categories of ecosystem services
- **Use context**: introductory chapter figure in a report
- **Tool chosen**: Gemini/Nano Banana, because the user wants a designed illustrative treatment
- **Text in image**: four short Chinese category labels
- **Aspect ratio**: 16:9 landscape
- **Style**: editorial scientific infographic, soft palette
- **Reference materials**: none

### Red-line check

- Real-data chart? No.
- Real geographic map? No.
- True network topology? No — conceptual categories, not a real ecosystem network.
- Specific numerical claims? No.
- Proceed. Soft warning: verify all Chinese text character by character.

### Template chosen

`template-infographic.md`.

### Delivery

````
## Image prompt for: Ecosystem services concept diagram

**Tool**: Gemini/Nano Banana
**Recommended parameters**:
- Aspect ratio: 16:9 landscape
- Quality/resolution: highest practical setting available
- Reasoning/thinking mode: use if available for multi-label layout
- Reference images: none

### English prompt (paste into Gemini/Nano Banana)
```
An editorial scientific infographic illustration designed as the introductory figure for a report chapter on ecosystem services.

The composition is a horizontal landscape divided into four equal columns. A unified stylized river runs across the bottom third of the image, visually connecting all four columns. Above the river, each column contains a small set of simple icons representing example services.

The four column headers, from left to right, are rendered exactly in Chinese:
1. "供给服务"
2. "调节服务"
3. "文化服务"
4. "支持服务"

Under "供给服务", show icons for fish, drinking water, and irrigation.
Under "调节服务", show icons for water purification, flood regulation, and climate regulation.
Under "文化服务", show icons for recreation, aesthetics, and education.
Under "支持服务", show icons for habitat, nutrient cycling, and biodiversity.

Use clean modern Chinese typography for the headers. Icons are equal-weight line illustrations in charcoal. The background is warm cream. The river is soft teal-blue with subtle hand-mixed-ink texture, not photorealistic.

Palette: warm cream background, deep teal river, charcoal icons/text, and four subtle accent colors used only in column header bands.

Avoid clip art, photorealistic textures, glowing effects, drop shadows, decorative flourishes, or generic AI illustration styling.

ASPECT RATIO: 16:9 landscape.
```

### Chinese parallel version (for audit, not for pasting)
```
一张编辑型科学信息图插图,用作报告中生态系统服务章节的引言图。

构图为横向画面,分成四个等宽列。一条统一的程式化河流横贯图像底部三分之一,在视觉上连接四列。河流上方,每列包含一组简单图标,代表该类别的示例服务。

四个列标题从左到右以中文准确渲染:
1. "供给服务"
2. "调节服务"
3. "文化服务"
4. "支持服务"

"供给服务"下方显示鱼、饮用水、灌溉图标。
"调节服务"下方显示水质净化、洪水调节、气候调节图标。
"文化服务"下方显示游憩、美学、教育图标。
"支持服务"下方显示栖息地、营养循环、生物多样性图标。

标题使用干净的现代中文字体。图标为等线重的炭灰色线条插图。背景为暖米色。河流为柔和青蓝色,带有轻微手调墨水质感,非照片级。

色板:暖米色背景、深青色河流、炭灰色图标和文字,四种柔和强调色仅用于列标题色带。

避免剪贴画、照片级纹理、发光效果、投影、装饰花纹或通用 AI 插画风格。

宽高比:16:9 横向。
```

### Post-processing notes
- Verify every Chinese character in the four headers.
- Verify column order.
- Verify icons are under the intended category.
- For formal publication, redo typography in a vector/layout tool.
````

---

## Example 3 — Refused real watershed map

### Brief captured

- **Figure**: a map of a real watershed showing infrastructure points, field sites, and waterbody extent
- **Use context**: study-area figure in a formal report
- **Tool requested**: ChatGPT/OpenAI image tool

### Red-line check

- Real geographic map? Yes — it needs real boundaries, watercourses, coordinates, and site locations.
- Red line triggered.

### Delivery

````
This figure should not be built with image generation.

A study-area map with real watershed boundaries, infrastructure points, field sites, and waterbody extent is a real geographic map. Image models can produce plausible-looking geography while inventing or shifting real features. For a formal report, that error is not defensible.

Use a GIS workflow instead:

1. Build the map in QGIS or ArcGIS with real spatial layers:
   - Watershed boundary
   - River network
   - Infrastructure or intervention points
   - Field-site or monitoring points
   - Reservoir, lake, or other waterbody polygon

2. Use publication symbology:
   - Removed or inactive infrastructure: crossed square
   - Monitoring stations: triangle or circle
   - Reservoir/lake: filled polygon
   - Add scale bar, north arrow, coordinate grid, and projection statement

3. Export:
   - SVG/PDF for publication
   - PNG for slides

If useful, I can produce a QGIS layout brief or a Mermaid/draw.io planning sketch, but not an image-generation prompt for this map.
````

---

## Example 4 — Multi-series prompt-set Markdown file

### Brief captured

- **Project**: visual prompt set for an environmental science presentation
- **Requested output**: Markdown file
- **Tool target**: ChatGPT/OpenAI GPT Image
- **Series**: cover concepts, scientific explainer figures, social media adaptations
- **Prompts per series**: 3
- **Shared style**: editorial scientific, restrained palette, no real data, no real maps

### Red-line check

- Real-data chart? No; all prompts are conceptual shells.
- Real geographic map? No.
- True network topology? No.
- Specific numerical claims? No.
- Proceed.

### Delivery shape

````
# environmental-science-visuals — Image Prompt Set

> Tool target: ChatGPT/OpenAI GPT Image
> Intended use: presentation and companion outreach visuals

## 0. Usage notes
Copy only the English prompt block into the image tool. Use the Chinese version for content audit. Add final labels and exact technical text manually where needed.

## 1. Shared assumptions and visual identity
- Style: editorial scientific, clean composition, restrained color.
- Palette: deep teal, warm cream, charcoal, one soft accent per series.
- Red-line status: no real data charts, real maps, or true network topology included.

## Series A: Cover Concepts
> Series goal: generate polished hero visuals for the opening slide.
> Variation axis: composition and mood.

### Prompt A1: Abstract River System Hero
**Tool**: ChatGPT/OpenAI GPT Image
**Recommended parameters**: 16:9, highest practical quality/resolution

#### English prompt
```
[standalone cover prompt]
```

#### Chinese parallel version
```
[complete Chinese audit version]
```

#### Post-processing notes
- Verify no unintended text appears.
- Adjust palette manually if brand colors must be exact.

## Series B: Scientific Explainer Figures
> Series goal: create conceptual scientific figure shells for technical explanation.
> Variation axis: viewpoint and level of detail.

### Prompt B1: Conceptual Habitat Cross-Section
...

## Series C: Social Media Adaptations
> Series goal: adapt the visual language into lower-density outreach images.
> Variation axis: aspect ratio and audience tone.

### Prompt C1: Square Outreach Visual
...

## Appendix: Red-line and QA checklist
- No prompt should be used for real-data charts, real maps, or true network topology.
- Verify text, morphology, proportions, and color semantics before publication.
````
