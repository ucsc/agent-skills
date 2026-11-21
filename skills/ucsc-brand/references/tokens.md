# UCSC Design Tokens — Full Reference

Read this whenever you need an actual hex/CSS/PMS value. Two sources, marked per section: **[Official]** = communications.ucsc.edu brand guide. **[Theme]** = the live `ucsc/ucsc-2022` WordPress theme's `theme.json` and SCSS.

## Primary colors [Official]

| Name | Hex | RGB | PMS Coated | PMS Uncoated |
|---|---|---|---|---|
| Primary Blue | `#003c6c` | 0, 60, 108 | 541C | 2945U |
| Primary Yellow (Gold) | `#fdc700` | 253, 199, 0 | 116 | 109U |

These are shared across all 10 UC campuses as a unifying element, and are the two colors UCSC uses most.

## Secondary colors [Official]

| Hex | RGB | PMS Coated | PMS Uncoated |
|---|---|---|---|
| `#006aad` | 0, 106, 173 | 300C | 3005U |
| `#13a5dc` | 19, 165, 220 | 299C | 2995U |
| `#007988` | 0, 121, 136 | 3145C | 3145U |
| `#f29813` | 242, 152, 19 | 1375C | 137U |
| `#ffbf00` | 255, 191, 0 | 1235C | 116U |
| `#93c02d` | (green) | 390C | 381U |
| `#da216d` (Rubine Red) | 218, 33, 109 | Rubine RedC | Rubine RedU |

Check contrast (WebAIM checker) whenever these are used as background/foreground text pairs — called out explicitly in the official guide.

## Extended palette [Theme]

The live theme registers a larger palette in `theme.json` — includes the official colors above plus these additions:

| Name | Hex | Slug | Notes |
|---|---|---|---|
| Black | `#000000` | `black` | |
| Dark Gray | `#595959` | `dark-gray` | |
| Light Gray | `#d9d9d9` | `light-gray` | |
| Lightest Gray | `#f5f5f5` | `lightest-gray` | |
| White | `#ffffff` | `white` | |
| Pacific Blue | `#13a5dc` | `ucsc-pacific-blue` | = official secondary `#13a5dc` |
| Ocean Blue | `#007988` | `ucsc-ocean-blue` | = official secondary `#007988` |
| University Yellow | `#ffbf00` | `ucsc-university-yellow` | = official secondary `#ffbf00` |
| Orange | `#f29813` | `ucsc-orange` | = official secondary `#f29813` |
| Green | `#93c02d` | `ucsc-green` | = official secondary green |
| Persimmon | `#ff6666` | `ucsc-persimmon` | theme-only addition, not in official guide |
| Rubine Red | `#da216d` | `ucsc-rubine-red` | = official Rubine Red |
| UCSC Royal Blue | `#1569a9` | `ucsc-royal-blue` | theme-only, used in gradients |
| UCSC Rubine Blue | `#0a3355` | `ucsc-rubine-blue` | theme-only, dark blue variant |
| Violator Gold | `#6F4A00` | `ucsc-violator-gold` | "Violator" colors — a design term for attention-grabbing badge/callout devices (e.g. a "New" or promo sticker breaking the normal grid). Use for badges/callouts, not body content. |
| Violator Yellow | `#fdf3d1` | `ucsc-violator-yellow` | pale badge background |
| Violator Pink | `#f3d8da` | `ucsc-violator-pink` | pale badge background |
| Violator Green | `#d5e6de` | `ucsc-violator-green` | pale badge background |

## Gradients [Theme]

| Name | CSS |
|---|---|
| UCSC Headline Gradient | `linear-gradient(90deg, #3e34b2 0%, #1569a9 50%, #79b9ad 100%)` |
| UCSC Header Gradient | `linear-gradient(90deg, #003c6c 29%, #1569a9 100%)` |
| UCSC Light Gradient | `linear-gradient(180deg, #ffffff 0%, #f2f2f2 100%)` |
| UCSC Image-with-Text Gradient | `linear-gradient(180deg, transparent 0%, #f2f2f2 30%, #000 90%)` (dark scrim for text-over-image legibility) |

Use these for their named purpose — headline text treatment, header bands, light section backgrounds, text-over-image scrims — not as generic decoration.

## Typography [Official + Theme]

**Primary typeface**: Roboto — chosen for readability, simplicity, accessibility. Recommended for large sizes, headings, headlines, and body copy alike.

**Real font stack (from theme.json)**:
```
Roboto, -apple-system, BlinkMacSystemFont, "Segoe UI", Oxygen-Sans, Ubuntu, Cantarell, "Helvetica Neue", sans-serif
```

**Serif option (theme.json)** — for editorial contrast, not a default:
```
Garamond, "Hoefler Text", "Times New Roman", Times, serif
```

**Case rules** [Official]:
- Sentence case: default for headings, body, buttons.
- Title Case: page titles only.
- ALL CAPS: primary navigation only (styled via CSS, not typed in caps).

## Type scale [Theme]

Fluid, modular scale (~1.2 ratio). `min`/`max` are the fluid clamp bounds.

| Slug | Size (rem) | Fluid min–max |
|---|---|---|
| small | .833rem | .79rem – .833rem |
| base | 1rem | .889rem – 1rem |
| one | 1.2rem | 1rem – 1.2rem |
| two | 1.44rem | 1.125rem – 1.44rem |
| three | 1.728rem | 1.266rem – 1.728rem |
| four | 2.074rem | 1.424rem – 2.074rem |
| five | 2.488rem | 1.602rem – 2.488rem |
| six | 2.986rem | 1.802rem – 2.986rem |
| seven | 3.583rem | 2.027rem – 3.583rem |
| eight | 5.16rem | 2.566rem – 5.16rem |

**Heading mapping actually used in the theme**:

| Element | Font size slug | Weight | Line-height |
|---|---|---|---|
| h1 | five (2.488rem) | 700 | 1.1 (small) |
| h2 | four (2.074rem) | 700 | 1.4 (x-large) |
| h3 | three (1.728rem) | 700 | 1.4 (x-large) |
| h4 | two (1.44rem) | 700 | 1.5 (xx-large) |
| h5 | one (1.2rem) | 700 | 1.5 (xx-large) |
| h6 | base (1rem) | 700 | 1.5 (xx-large) |
| body | base (1rem) | — | 1.5 (xx-large) |

## Line-height scale [Theme]

| Slug | Value |
|---|---|
| baseline | 1 |
| small | 1.1 |
| medium | 1.2 |
| large | 1.3 |
| x-large | 1.4 |
| xx-large | 1.5 |

## Spacing scale [Theme]

| Slug | Value |
|---|---|
| x-small | .555rem |
| small | .889rem |
| baseline | 1.266rem |
| medium | 1.802rem |
| large | 2.281rem |
| outer | = small (1.802rem) |

Larger section-level spacing tokens (fluid, clamp-based):

| Slug | Clamp value |
|---|---|
| 20 | clamp(1rem, 2vw, 1.5rem) |
| 30 | clamp(1.5rem, 5vw, 2rem) |
| 40 | clamp(1.8rem, ..., 3rem) |
| 50 | clamp(2.5rem, 8vw, 4.5rem) |
| 60 | clamp(3.75rem, 10vw, 7rem) |
| 70 | clamp(5rem, ..., 8rem) |
| 80 | clamp(7rem, 14vw, 11rem) |

## Layout [Theme]

- Content max-width: `80rem` (1280px)
- Border radius (root/default): `0` — sharp corners
- Link color: primary blue (`--wp--preset--color--ucsc-primary-blue`)

## Buttons [Theme]

- Shape: fully rounded pill — `border-radius: 100px`
- Border: `2px solid` (color matches variant)
- Padding: `calc(0.32em + 2px) calc(2.5em + 2px)`
- Transition: `0.25s ease-in-out` on hover/focus/active

| Variant class | Default | Hover/focus |
|---|---|---|
| `.is-style-ucsc-black` | black bg, white text | white bg, black text |
| `.is-style-ucsc-blue` | primary blue bg, white text | white bg, primary blue text |
| `.is-style-ucsc-gold` | primary yellow bg, primary blue text | inverts similarly |
| `.is-style-ucsc-ocean` | ocean blue bg, white text | white bg, ocean blue text |
| `.is-style-ucsc-white` | white bg, primary blue text/border | — |
| `.is-style-ucsc-outline-white` | transparent bg, white text/border | — |

Pattern: **fill and text color swap on hover** — not a shadow, scale, or opacity effect.

## Logo colors [Official]

Only three permitted: Santa Cruz blue (`#003c6c`), black, white (reversed). Never any other color, never distorted, never with drop shadows.

- Minimum size: 60px tall (online), 1.5in wide (print)
- Safe space: roughly half the logo's own width, clear on all sides
