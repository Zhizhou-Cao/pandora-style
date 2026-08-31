# External Style Skill Registry

This registry contains complete Style Skills installed separately under
`${CODEX_HOME:-$HOME/.codex}/skills/`. They are adapters, not additional rows in the
108-style built-in catalog. Read the selected external `SKILL.md` completely at
runtime, then localize its visual language through the Regional Style Contract.

## Selector Syntax

- `external:<skill-name>` selects the complete Skill.
- `external:<skill-name>/<variant>` selects a named mode, style, preset, or
  theme inside that Skill.
- A bare installed Skill name remains valid, for example
  `$photo-riso-poster`.

## Direct Photo and Poster Adapters

| Selector | Installed source | Regional use | License |
|---|---|---|---|
| `external:gc-minimal-zine-poster-v0-1` | local original | quiet zine paper, halftone/xerox wear, restrained type, one source-justified accent | local package |
| `external:scenes-gathered-zine-v1-3` | local original | truthful-photo and paper-illustration continuity, torn or printed transitions | local package |
| `external:ni-poster/scene-distillation` | `ttttstc/ni-skill` | authored source-derived illustration and visual metaphor inside masks; do not import its global no-photo rule | MIT plus bundled upstream notices |
| `external:ni-poster/photo-abstract-editorial` | `ttttstc/ni-skill` | clean editorial abstraction and source-derived memory-panel language inside masks | MIT plus bundled upstream notices |
| `external:photo-riso-poster` | `luckdvr/photo-riso-poster` | 2–3 ink risograph, evidence-led abstraction, count/interval/direction preservation | MIT |
| `external:ink-wash-poster` | `TwentyfiveBTea/ink-wash-poster` | contemporary ink, water, absorption, paper and restrained editorial marks | AGPL-3.0; keep as a separate unmodified package |
| `external:photo-evidence-ledger` | `byJming/photo-skills-atelier` | geometry, interval and color evidence specimens; local labels only when useful | MIT |
| `external:photo-small-world-revival` | `byJming/photo-skills-atelier` | sparse hand-drawn subject/companion relation with one localized source hue | MIT |
| `external:torn-paper-collage-poster` | `agentara/skills` | layered torn paper, archive scraps, tape, stamps, halftone and photocopy grain | MIT |

`ni-poster/standard` and `ni-poster/gathered` deliberately alias the two local
originals above. Do not count or select them as extra styles.

## Editorial Vision Studio Variants

Use `external:editorial-vision-studio/<variant>`. The complete package is MIT
licensed and installed from `Yu-0312/editorial-vision-studio`.

Style variants:

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

Preset variants:

- `ivory-postcard`
- `papercraft-diorama-postcard`
- `vintage-travel-poster`

Read both its root `SKILL.md` and the selected `styles/<variant>.md` or
`presets/<variant>.md`. Use its visual language and recovery logic, but discard
its global layout template.

## Dynamic Style Engines

These generate a new style system rather than selecting one fixed look:

| Selector | Output used by this Skill | License |
|---|---|---|
| `external:canvas-design` | an original visual philosophy translated into palette, form, space, composition and mark rules | Apache-2.0 |
| `external:algorithmic-art` | an original computational philosophy translated into fields, particles, flows, noise, repetition and seeded variation | Apache-2.0 |

Do not execute their full-canvas artifact workflow for regional transfer. Use
their philosophy stage to produce a Regional Style Contract, then render that
contract only inside the selected masks.

## Palette-Only Adapter

`external:theme-factory/<theme>` supplies color and typographic tendencies, not
a complete image medium. Pair it with a built-in or external medium. Available
Apache-2.0 themes:

- `ocean-depths`
- `sunset-boulevard`
- `forest-canopy`
- `modern-minimalist`
- `golden-hour`
- `arctic-frost`
- `desert-rose`
- `tech-innovation`
- `botanical-garden`
- `midnight-galaxy`

Theme Factory never overrides the source-derived color policy automatically.
Use it only when the user names the theme or explicitly asks for palette-led
exploration.

## Mask-First Invariant

The region mode controls the **outer silhouette**. The external style controls
only the **internal rendering**.

- In `line-guided-geometry`, every final outer mask must remain a legible
  rectangle, trapezoid, parallelogram, wedge, triangle, or other source-line
  polygon. Torn fibers, ink bleed, particles, collage scraps, or semantic
  contours may appear inside it but cannot replace its geometric boundary.
- In `semantic-fragments`, every final outer mask must remain an incomplete
  source-object, atmosphere, reflection, shadow, or material contour. Internal
  grids, facets, blocks, or paper pieces cannot turn it into a box.
- In `semantic-expanded`, use the same source-contour logic at 32–52% coverage.
  Larger or linked masks may include one nearly complete object cluster, but
  must preserve tapering edges, photographic gaps, and at least two substantial
  untouched photo fields. It is not permission for a global style filter.
- Judge the mode from the outer mask silhouette at thumbnail scale. If a viewer
  cannot distinguish the two modes without reading the label, reject and
  regenerate once.

## Excluded Candidates

- `torn-photo-window-sketch-zine`: no explicit license found; not installed.
- `travel-memory-sticker-card`: personal-use-only license; not installed into
  this reusable collection.
- Generic prompt optimizers and image-generation wrappers: not Style Skills and
  therefore not counted.
- Online mirrors of the two local originals: duplicates, not installed.

## Provenance

- Anthropic Skills: https://github.com/anthropics/skills
- ni-poster: https://github.com/ttttstc/ni-skill/tree/main/skills/ni-poster
- Editorial Vision Studio: https://github.com/Yu-0312/editorial-vision-studio
- Photo Riso Poster: https://github.com/luckdvr/photo-riso-poster
- Ink Wash Poster: https://github.com/TwentyfiveBTea/ink-wash-poster
- Photo Skills Atelier: https://github.com/byJming/photo-skills-atelier
- Torn Paper Collage Poster: https://github.com/agentara/skills/tree/main/skills/aigc/torn-paper-collage-poster
