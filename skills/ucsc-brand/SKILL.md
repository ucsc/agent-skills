---
name: ucsc-brand
description: UC Santa Cruz visual identity — official blue/gold colors, Roboto typography, logo rules, and brand voice, combined with the real token values from the ucsc-2022 WordPress theme (extended color palette, button styles, spacing/type scale). Use this whenever building or styling ANYTHING visual that represents UC Santa Cruz — web pages, mockups, email newsletters, presentations, decks, flyers, one-pagers, social graphics, dashboards. Consult this by default for UCSC-related visual work even if the request doesn't say "branded," "official," or "on-brand" — assume UCSC visual work should follow this identity unless told otherwise.
---

# UC Santa Cruz Brand

Sources: the official brand guide at communications.ucsc.edu (colors, typography, logo, voice) and the `ucsc/ucsc-2022` WordPress theme repo (real implementation values — extended palette, button treatment, type/spacing scale). Full token tables are in `references/tokens.md` — read that before generating any actual color/CSS values; this file is the rules and judgment calls.

## Quick reference

- **Primary colors**: UCSC Blue `#003c6c`, UCSC Gold `#fdc700`. These carry the most weight — lean on them first.
- **Primary typeface**: Roboto. Sentence case for nearly everything (headings, buttons, copy). No ALL CAPS except primary nav.
- **Voice**: smart, confident, bold. Can be snappy and witty. Never corporate-dry.
- **Shape language**: sharp corners everywhere (border-radius 0), *except* buttons, which are full pills (border-radius 100px). This contrast is a real, deliberate pattern in the theme — don't round other elements and don't square off buttons.

## Color

Blue and gold are the two colors UCSC uses most — bold, flat swatches, not tints or screens. The official guide is explicit: "we very rarely use tints or screens of our colors." Reach for a secondary color (there's a real palette of 7, plus theme extensions — see references) before reaching for a lighter/darker shade of blue.

When choosing from the full palette (references/tokens.md has hex + usage), default to primary blue/gold for anything representing the university broadly. Secondary and theme-extended colors are for accents, categorization (e.g. distinguishing sections/divisions), or data visualization where you need more than two colors.

Always check contrast when colors are used as background/foreground text pairs — this is called out explicitly in the official guide, not just a general accessibility nicety.

## Typography

Roboto is the primary typeface for everything — headings, headlines, and body copy. The real font stack (from the live theme) has solid system-font fallbacks; use it exactly as given in references/tokens.md so things render consistently even where Roboto isn't loaded (e.g. email clients — see the Email section below).

There's also a serif option (Garamond-led stack) baked into the theme for editorial contrast — an option, not a replacement for Roboto as the default.

**Case rules** (from the official editorial guide, followed exactly):
- Sentence case for nearly everything: headings, body copy, buttons.
- Title Case only for page titles.
- No ALL CAPS anywhere except primary navigation (and even nav should be *entered* as normal case and capitalized via CSS, not typed in caps).

**Type scale**: the theme uses a real fluid modular scale (ratio ~1.2), not arbitrary sizes. Use the scale in references/tokens.md rather than inventing font sizes — h1 is large and tight (line-height 1.1), body and small headings run more relaxed (line-height 1.4–1.5).

## Voice

Smart, confident, and bold. Embrace passion, diversity, and striving for positive change — UCSC's own words. Writing can be conversational and a little snappy/witty when the context allows (a newsletter, a social caption) — this isn't a stiff institutional voice. Genuine feeling over generic corporate polish.

## Logo — read before touching

The UCSC logo is a protected mark. Don't attempt to redraw, approximate, or hand-generate it (as SVG, in an image model, whatever) — that's both a trademark issue and something no AI-generated version will get right anyway. Instead:

- Leave a clearly-marked placeholder (e.g. a box labeled "UCSC logo") wherever a design calls for it, and tell the person to drop in the real file.
- Point to the official files if asked: communications.ucsc.edu/brand-overview/logos-imagery has print and digital download links.
- If you know the rules are relevant, mention them: logo only appears in Santa Cruz blue, black, or white (reversed) — never other colors; needs safe space around it (roughly half the logo's own width); minimum 60px tall online; never stretched, shadowed, or placed on a busy/clashing background.
- Departments use a standard "lockup" (logo + department name) rather than custom logos — worth knowing if a design brief is for a specific department, school, or program rather than the university broadly.

## Layout & component patterns (from the real theme)

These are patterns actually implemented in `ucsc-2022`, not just guide-book theory — use them for anything web/UI-shaped:

- **Buttons are full pills** (border-radius 100px), with a 2px border, generous horizontal padding, and a 0.25s ease-in-out transition. The real button variants invert on hover/focus: a filled blue button becomes white-fill/blue-text on hover, filled gold becomes white-fill/gold-text, etc. — fill-swaps-with-text-color is the hover pattern, not a shadow or scale effect.
- **Everything else is sharp-cornered** (border-radius 0 at the root level) — cards, images, containers. Don't add rounded corners to non-button elements; it's not part of this identity.
- **Content max-width is 1280px** (`80rem`) for primary content areas.
- **Gradients exist and are used deliberately** for specific moments (headline text, header bands, light section backgrounds) — see references/tokens.md for the actual gradient values. These aren't decoration to sprinkle everywhere; they mark specific structural moments (a hero header, a headline).
- **White space is intentional.** The official guide states it plainly: "we like white space! It allows color to pop and type to breathe." Don't crowd bold color blocks with clutter.

## Per-deliverable notes

**Web pages / mockups / dashboards**: Use the theme.json tokens directly (colors, type scale, spacing scale) — see references/tokens.md. Sharp corners, pill buttons, Roboto, sentence case, 1280px content width.

**Email** (newsletters, campaigns): Build with inline styles and table layout for client compatibility (this is a hard email constraint, not a UCSC-specific one). Use the Roboto font stack's *system fallback* portion, since Roboto itself won't load in most email clients — Arial/Helvetica is the safe default; the brand identity survives fine through color and voice even when the exact typeface doesn't render. Blue/gold still carry the identity. Keep the sentence-case rule.

**Print / decks / flyers**: PMS and CMYK values are in references/tokens.md alongside the hex codes, for anything headed to print. Bold flat color blocks translate well to slides and print — this identity was designed with print in mind from the start ("bold swatches of color are a common element in our designs").

**Social graphics**: Bold color, confident short-form copy in the brand voice, sentence case captions.

## What NOT to default to

UCSC's real look is bold flat color, sharp corners with pill buttons, Roboto in sentence case, and generous white space. It is specifically *not*: a warm cream/off-white background, tracked-out ALL-CAPS eyebrow labels, soft-grey-shadow rounded "SaaS cards," or middot-separated meta strings — these are generic AI-design defaults that have nothing to do with this identity, and they'll clash with it if they creep in.

## Freshness note

Color/logo/typography rules pulled from communications.ucsc.edu and websites.ucsc.edu (official guide pages, last modified between Jun 2025 and May 2026 as of this writing). Theme token values pulled directly from the `ucsc/ucsc-2022` GitHub repo on 2026-09-04. That repo is actively developed — if it's been a long time since this skill was written, or something here looks stale, it's worth re-pulling `theme.json` and the `src/scss/` files rather than trusting this blindly.
