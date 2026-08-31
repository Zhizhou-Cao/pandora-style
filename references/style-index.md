# Style Catalog Index

## Selection Flow

1. Match the source structure and requested mood to a family below.
2. Prefer a style whose `fit` includes the requested mode.
3. Prefer source-resonant media over fashionable but unrelated effects.
4. Avoid repeating the same family in a comparison unless the user wants controlled variants.
5. Load only the selected family file before compiling the prompt.

## Families

| Family | File | Count | Use when |
|---|---|---:|---|
| Print and reproduction | [styles-print.md](styles-print.md) | 18 | tactile ink, zine, archival, poster, graphic texture |
| Photography and darkroom | [styles-photo.md](styles-photo.md) | 18 | tonal, chemical, optical, film, exposure effects |
| Art and design movements | [styles-movements.md](styles-movements.md) | 18 | explicit compositional grammar or historical graphic language |
| Painting and drawing | [styles-drawing.md](styles-drawing.md) | 18 | hand-made marks, washes, contours, painterly fragments |
| Material and craft | [styles-craft.md](styles-craft.md) | 18 | textile, glass, ceramic, paper, mosaic, tactile construction |
| Digital and geometric | [styles-digital.md](styles-digital.md) | 18 | pixels, glitches, tessellation, computational structure |

Total catalog styles: **108**.

This number covers only lightweight built-in recipes. Complete installed Style
Skills and their variants are maintained separately in
[external-style-skills.md](external-style-skills.md); they are not silently
folded into the 108 count.

## Source-to-Family Routing

- Strong architecture, roads, horizons, or perspective: print, movements, drawing, digital.
- Faces, figures, animals, plants, clouds, smoke, or water: photo, drawing, craft, semantic-friendly print.
- Dense repeated detail: print rhythm, embroidery, mosaic, dithering, pixel, or contour compression.
- Quiet atmospheric scenes: platinum, salt print, gum bichromate, ink wash, watercolor, color field.
- High-energy urban scenes: constructivist, futurist, screenprint, glitch, chromatic shift.
- Strong local colors: source-resonant screenprint, pochoir, gouache, stained glass, ceramic transfer.
- Nearly monochrome scenes: cyanotype, duotone offset, solarization, aquatint, charcoal.

## Compatibility Labels

- `both`: works well with both modes.
- `geometry`: strongest with line-guided geometry; semantic use needs simplification.
- `semantic`: strongest with contour-following fragments; geometry use should follow a real plane.

## Color Defaults

Catalog palette descriptions are tendencies, not mandatory hues. Apply the Skill color priority first. Only process-defining styles such as cyanotype, thermal imaging, and infrared false color may override with a process-native palette.

## Style Skill Overrides

Installed Style Skills such as `gc-minimal-zine-poster-v0-1` and `scenes-gathered-zine-v1-3` remain valid external adapters. When invoked, their full instructions outrank a catalog recipe, except that this Skill always localizes global canvas and layout rules to selected regions.

For online-installed packages, named variants, dynamic style engines, license
notes, selector syntax, and duplicate handling, read
[external-style-skills.md](external-style-skills.md). Prefer direct photo/poster
adapters for source-specific transformations; use dynamic engines only when the
user wants a newly invented visual system; use Theme Factory only as an
explicit palette layer.

## Research Basis

The catalog uses movements and material processes rather than living-artist imitation. Definitions were checked against museum and institutional references collected in [sources.md](sources.md).
