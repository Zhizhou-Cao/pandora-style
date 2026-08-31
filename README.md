# Pandora Style

A source-aware regional photo stylization Skill for Codex. It preserves the original photograph outside selected regions while applying one of 108 built-in styles, an installed external Style Skill, or a dynamically created visual language inside those regions.

面向 Codex 的照片局部风格转换 Skill：未选区域保留真实照片，只在来源明确的几何或语义区域内应用内置风格、外部 Style Skill 或动态生成的视觉语言。

- [中文说明](#中文说明)
- [English Guide](#english-guide)
- [Skill instructions](SKILL.md)

## Installation / 安装

Clone or download this repository, then place the complete folder at `${CODEX_HOME:-$HOME/.codex}/skills/pandora-style`. Restart Codex after installation.

克隆或下载仓库后，将完整文件夹放到 `${CODEX_HOME:-$HOME/.codex}/skills/pandora-style`，然后重启 Codex。

```bash
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
cp -R pandora-style "${CODEX_HOME:-$HOME/.codex}/skills/pandora-style"
```

The 108 built-in styles are self-contained. Selectors beginning with `external:` require the corresponding third-party Skill to be installed separately.

108 种内置风格可直接使用；以 `external:` 开头的选择器需要另外安装对应的第三方 Skill。

---

## 中文说明


## 简介

`pandora-style` 是一个照片局部风格转换 Skill。它先分析照片的主体、构图、透视、线条、色彩和物体轮廓，再选择少量与原图有关的区域，只在这些区域内改变视觉风格。未选中的部分继续保留为真实照片。

它适合制作：

- 写实与抽象并存的艺术照片
- 局部印刷、绘画、拼贴或数字效果
- 同一照片在不同区域模式下的对照实验
- 将其他完整 Style Skill 局部套用到照片中
- 根据照片动态创造新的视觉风格

## 核心原则

区域模式决定“哪里发生变化，以及外轮廓是什么”；风格决定“区域内部如何表现”。

例如，同一个 Riso 风格可以分别放进几何切片、克制语义碎片或扩展语义区域。三张图的印刷材质可以相同，但区域形态和覆盖程度必须明显不同。

所有模式都应尽量保持原图的画幅、视角、透视、光线、主体身份和未选区域的自然色彩。

## 三种区域模式

### `line-guided-geometry`

沿照片中的结构线创建通常 3–4 个不等大的几何区域。

- 可使用长方形、梯形、平行四边形、三角形或楔形。
- 区域跟随屋檐、道路、地平线、建筑垂线、阴影或透视轴。
- 通常覆盖画面的 15–30%。
- 大小和长宽比应有所变化，可以轻微重叠。
- 避免平均网格、整齐方块、随意漂浮和过大的角落色块。

适合建筑、城市、街景、室内空间和其他结构线明确的照片。

### `semantic-fragments`

沿真实物体或自然现象的轮廓创建通常 3–4 个克制、不完整的语义碎片。

- 可选择云、烟、人物、植物、建筑、倒影、阴影、屋檐或材质边缘。
- 通常覆盖画面的 15–30%。
- 保留断口、空隙、遮挡、渐隐和反射衰减。
- 默认只选择物体的一部分，而不是完整抠图。
- 避免矩形框、贴纸边缘、完整孤立剪影和无来源的圆滑色块。

适合希望保留更多原片、只进行局部艺术介入的情况。

### `semantic-expanded`

使用相同的语义轮廓逻辑，但创建通常 3–5 个更大或相互呼应的区域。

- 通常覆盖画面的 32–52%。
- 可以处理一个接近完整的物体或物体群。
- 区域之间可以通过方向、节奏或材质形成联系。
- 必须保留至少两个分布在不同位置的大块真实照片区域。
- 仍需保留渐隐边缘、遮挡、断口或原片空隙。
- 不允许演变成全图滤镜或把所有主要场景层同时转换。

适合希望画面更沉浸、更完整、更接近独立艺术作品的情况。

## 风格来源

### 108 种内置风格

内置风格分为六个家族，每个家族 18 种：

| 风格家族 | 适用方向 |
|---|---|
| 印刷与复制 | Riso、复印、网点、版画、档案纸张和图形纹理 |
| 摄影与暗房 | 胶片、曝光、化学显影、色调和光学效果 |
| 艺术与设计运动 | 明确的构图语法和历史图形语言 |
| 绘画与手绘 | 水墨、水彩、炭笔、线稿、颜料和手工笔触 |
| 材料与工艺 | 纸艺、纺织、刺绣、玻璃、陶瓷和马赛克 |
| 数字与几何 | 像素、故障、镶嵌、计算结构和几何系统 |

### 外部完整 Style Skill

可以使用 `external:<skill-name>` 或直接使用已安装的 Skill 名称：

- `gc-minimal-zine-poster-v0-1`
- `scenes-gathered-zine-v1-3`
- `ni-poster/scene-distillation`
- `ni-poster/photo-abstract-editorial`
- `photo-riso-poster`
- `ink-wash-poster`
- `photo-evidence-ledger`
- `photo-small-world-revival`
- `torn-paper-collage-poster`

系统不会照搬这些 Skill 的全画布比例或整体海报布局，而是提取其材质、色彩、线条、抽象方式、边缘处理和负面约束，再局部应用到选定区域。

### Editorial Vision Studio

调用形式：

```text
external:editorial-vision-studio/<variant>
```

可用风格包括：

- `apartamento`
- `brutalist`
- `cos`
- `kinfolk`
- `monocle`
- `muji`
- `popeye`
- `purple`
- `swiss`
- `travel-poster`
- `wallpaper`
- `ivory-postcard`
- `papercraft-diorama-postcard`
- `vintage-travel-poster`

### 动态风格引擎

- `external:canvas-design`
- `external:algorithmic-art`

动态引擎不是选择一个固定滤镜，而是根据照片创建新的视觉哲学和区域风格合约，包括风格名称、空间关系、形状、色彩、材料、节奏、抽象程度和边缘行为。

### 调色板层

`external:theme-factory/<theme>` 可以提供颜色与字体倾向，但它不是独立的图像媒介，应与内置或外部风格组合使用。

## 自动分析与配色

每次处理前，Skill 会建立一个 Scene Card，记录：

- 核心主体和辅助元素
- 构图、透视和空间关系
- 主导线条和视觉重量
- 安静区域与密集区域
- 原生主色和有意义的小面积色彩
- 几何候选线与语义候选轮廓

配色优先级为：

1. 强化照片中已有的有意义小面积色彩。
2. 使用与原图相近但更清晰的颜色。
3. 原图缺少可用颜色时，加入克制的互补色。
4. 仅在媒介本身要求时使用工艺固定色，例如蓝晒蓝。
5. 只有用户明确要求时才完全随机。

## 常用调用方式

### 指定模式和风格

```text
用 $pandora-style 处理这张照片。

模式使用 semantic-expanded。
风格使用 external:photo-riso-poster。
生成一张最终图片。
```

### 自动选择风格

```text
用 $pandora-style 处理这张照片。

模式使用 line-guided-geometry 和 semantic-fragments。
从内置与外部风格中选择最适合照片的两种，
不要来自同一个风格家族。
每种模式与风格组合生成一张。
```

### 动态创建原创风格

```text
用 $pandora-style 处理这张照片。

模式使用 semantic-expanded。
调用 external:canvas-design，
根据照片创建一种原创视觉语言并生成一张图片。
```

### 三种模式对照

```text
使用同一个风格，分别生成：

line-guided-geometry
semantic-fragments
semantic-expanded

保持颜色、材质和抽象程度一致，共生成三张。
```

## 输出与质量检查

最终图片使用 `mode × style-slug` 标注。系统会检查：

- 未选区域是否继续保持原片。
- 风格是否泄漏到全图。
- 几何模式和语义模式是否能通过外轮廓区分。
- 两档语义覆盖是否符合各自范围。
- 添加的颜色是否来源明确且具有结构作用。
- 是否出现无关文字、边框、新物体、假水印或错误数量。

如果生成结果出现明确失败，系统最多针对该问题修正一次。被拒绝的草稿不计入用户要求的最终图片数量。

## 文档说明

- [`SKILL.md`](SKILL.md) 是提供给 Codex 的英文执行规范。
- 本节是面向使用者的中文说明。
- [跳转到英文用户说明](#english-guide)。


---

## English Guide


## Overview

`pandora-style` is a skill for localized photo stylization. It analyzes the subject, composition, perspective, structural lines, colors, and semantic contours of a photograph, then changes the visual style only inside a small set of source-aware regions. Everything outside those regions remains anchored in the original photograph.

It is useful for:

- Mixed-realism artworks that combine photography and abstraction
- Localized print, painting, collage, craft, or digital treatments
- Controlled comparisons between different region modes
- Applying a complete external Style Skill only inside selected areas
- Inventing a new visual system dynamically from the source photograph

## Core Principle

The region mode decides where transformation occurs and what the outer mask looks like. The style decides how the inside of that mask is rendered.

For example, the same risograph language can be used inside geometric slices, restrained semantic fragments, or expanded semantic fields. The material may remain consistent across all three images, while their region shapes and coverage must remain visibly different.

Every mode should preserve the source crop, viewpoint, perspective, lighting, subject identity, and natural color outside the transformed regions.

## Region Modes

### `line-guided-geometry`

Creates normally 3–4 unequal geometric regions derived from dominant source lines.

- Regions may be rectangles, trapezoids, parallelograms, triangles, or wedges.
- They follow rooflines, roads, horizons, building verticals, shadows, or perspective axes.
- Normal transformed coverage is 15–30%.
- Size and aspect ratio should vary; minor overlap is allowed.
- Avoid uniform grids, identical squares, arbitrary floating shapes, and oversized corner blocks.

Best suited to architecture, cityscapes, streets, interiors, and other photographs with strong structural lines.

### `semantic-fragments`

Creates normally 3–4 restrained, incomplete masks that follow real subjects or natural phenomena.

- Masks may follow clouds, smoke, people, plants, buildings, reflections, shadows, eaves, or material edges.
- Normal transformed coverage is 15–30%.
- Preserve interruptions, gaps, occlusion, fading atmosphere, and reflection decay.
- Select partial objects by default rather than complete cutouts.
- Avoid rectangular panels, sticker outlines, isolated complete silhouettes, and generic blobs.

Best suited to subtle intervention when most of the original photograph should remain visible.

### `semantic-expanded`

Uses the same source-contour logic with normally 3–5 larger or visually connected regions.

- Normal transformed coverage is 32–52%.
- One nearly complete object or object cluster may be transformed when compositionally useful.
- Related regions may echo or connect through direction, rhythm, or material.
- At least two substantial untouched photographic fields must remain in different parts of the frame.
- Tapering edges, occlusion gaps, interruptions, or natural-photo openings must remain visible.
- It must not collapse into a global filter or transform every major scene layer at once.

Best suited to immersive, expressive results that read more like independent artworks.

## Style Sources

### 108 Built-in Styles

The built-in catalog contains six families with 18 styles each:

| Family | Typical use |
|---|---|
| Print and reproduction | Risograph, xerox, halftone, printmaking, archival paper, graphic texture |
| Photography and darkroom | Film, exposure, chemical, tonal, and optical effects |
| Art and design movements | Explicit compositional systems and historical graphic languages |
| Painting and drawing | Ink wash, watercolor, charcoal, linework, paint, and hand-made marks |
| Material and craft | Paper, textile, embroidery, glass, ceramic, and mosaic treatments |
| Digital and geometric | Pixels, glitches, tessellation, computational structures, and geometric systems |

### Complete External Style Skills

Use `external:<skill-name>` or name an installed skill directly:

- `gc-minimal-zine-poster-v0-1`
- `scenes-gathered-zine-v1-3`
- `ni-poster/scene-distillation`
- `ni-poster/photo-abstract-editorial`
- `photo-riso-poster`
- `ink-wash-poster`
- `photo-evidence-ledger`
- `photo-small-world-revival`
- `torn-paper-collage-poster`

The system does not copy their global canvas ratio or full-poster layout. It extracts locally renderable material, color, line, abstraction, edge behavior, and negative constraints, then applies those rules only inside the selected masks.

### Editorial Vision Studio

Selector format:

```text
external:editorial-vision-studio/<variant>
```

Available variants include:

- `apartamento`
- `brutalist`
- `cos`
- `kinfolk`
- `monocle`
- `muji`
- `popeye`
- `purple`
- `swiss`
- `travel-poster`
- `wallpaper`
- `ivory-postcard`
- `papercraft-diorama-postcard`
- `vintage-travel-poster`

### Dynamic Style Engines

- `external:canvas-design`
- `external:algorithmic-art`

Dynamic engines do not select a fixed filter. They create an original visual philosophy and a Regional Style Contract from the photograph, including a style name, spatial logic, shapes, color, material, rhythm, abstraction level, and edge behavior.

### Palette Layer

`external:theme-factory/<theme>` supplies color and typographic tendencies. It is not a complete image medium and should be paired with a built-in or external style.

## Source Analysis and Color

Before generation, the skill builds a Scene Card containing:

- Primary and supporting subjects
- Composition, perspective, and spatial relationships
- Dominant lines and visual-weight distribution
- Quiet and dense areas
- Native colors and meaningful minor colors
- Candidate geometric axes and semantic contours

Color priority is:

1. Intensify a meaningful minor color already present in the source.
2. Use a clearer analogous source hue.
3. Add a restrained complementary hue when the source has no useful minor color.
4. Use a process-native color only when essential, such as cyanotype blue.
5. Use fully random color only when explicitly requested.

## Common Usage Patterns

### Specify a mode and style

```text
Use $pandora-style on this photograph.

Mode: semantic-expanded.
Style: external:photo-riso-poster.
Generate one final image.
```

### Let the skill select styles

```text
Use $pandora-style on this photograph.

Use line-guided-geometry and semantic-fragments.
Choose the two most suitable styles from the built-in and external catalog,
and do not choose both from the same family.
Generate one image for each mode and style combination.
```

### Create an original dynamic style

```text
Use $pandora-style on this photograph.

Mode: semantic-expanded.
Use external:canvas-design to create an original visual language
from the photograph, then generate one image.
```

### Compare all three modes

```text
Use the same style to generate:

line-guided-geometry
semantic-fragments
semantic-expanded

Keep color, material, and abstraction level constant. Generate three images.
```

## Output and Quality Control

Each final image is labeled `mode × style-slug`. The skill checks that:

- Unselected areas still read as the source photograph.
- Style has not leaked across the whole frame.
- Geometric and semantic modes remain distinguishable through their outer masks.
- Each semantic tier respects its intended coverage.
- Added color is source-justified and structurally useful.
- No unwanted typography, frame, invented object, watermark, or extra final image appears.

If the result has a concrete failure, the skill performs at most one targeted correction. Rejected drafts do not count toward the requested number of final images.

## Documentation Notes

- [`SKILL.md`](SKILL.md) is the English execution specification read by Codex.
- This section is the English user guide.
- [Jump to the Chinese user guide](#中文说明).
