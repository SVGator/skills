# Color — commit to a palette, and never the default one

Color is the fastest thing the eye judges and the first place generated work gives itself away. A timid, evenly-spread palette reads as "AI made this"; a committed palette with a dominant field and one sharp accent reads as designed. In an SVG asset color lives in `fill.paint`, `stroke.paint`, and gradient stops — and it doubles as a motion channel, since a shift *to* a color carries state (→ [../reference/property-meaning.md](../reference/property-meaning.md)). Get the static palette right first; the motion inherits it.

## Pick the brand's actual hue — not the reflex

The single biggest tell is reaching for the same defaults every time. Do not open on blue (hue ~250) or warm orange (hue ~60) by habit — those are the dominant generated-design hues, not the right answer for any specific piece. Read the subject and the brand, choose *its* hue, and build everything from there.

**Banned palettes** — these are instantly recognizable as machine output:
- cyan-on-dark / teal glow on near-black,
- purple→blue gradients (the "AI purple" aesthetic),
- neon accents burning on a dark background,
- oversaturated everything with no neutral to rest against.

If your first instinct lands on one of these, it's the trained reflex. Choose again.

## Think in OKLCH, even when you output hex

OKLCH is perceptually uniform: equal steps in lightness *look* equal (HSL does not deliver this — 50% lightness in yellow looks bright, in blue looks dark). To build a color and its lighter/darker variants, hold chroma and hue roughly constant and move lightness — but **drop chroma as you approach white or black.** High chroma at extreme lightness looks garish and plasticky. A light tint at 85% lightness wants low chroma (~0.08), not the 0.15 of its mid-tone parent. This keeps a set of shades feeling like one family instead of a rainbow.

## Tint the neutrals toward the hue

Pure gray is dead next to color. Give every "neutral" a whisper of chroma (roughly 0.005–0.015) hued toward the piece's brand color. It's too small to read as "tinted" consciously, but it quietly binds the neutrals to the accent so the whole thing feels of a piece. Tint toward *this* piece's hue — not always-warm or always-cool, which are their own monoculture.

## 60 / 30 / 10 — by visual weight, not pixel count

- **60%** — the dominant field / neutral ground the piece sits on.
- **30%** — secondary marks, supporting shapes, outlines.
- **10%** — the accent: the one color that means "look here."

The accent works *because it is rare.* The classic mistake is flooding the piece with the brand color because it's "the brand color" — overuse kills its power. Reserve it for the hero and the moment that matters (including the color the motion resolves *to*).

## Never pure black or pure white

`#000` and `#fff` don't exist in nature — real surfaces carry a cast. Use a very dark tinted near-black (think ~12–18% lightness with a hint of the hue) and an off-white with the same faint tint. Large fields of pure black especially read as cheap and flat.

## One accent is usually enough

Most pieces work with a single accent over a neutral field. A second and third color is decision fatigue and visual noise more often than it's richness. Add another hue only when it *means* something (a second semantic state, a two-brand mark). Skip secondary/tertiary unless the piece genuinely needs them.

## Contrast and legibility — especially at size

- Keep meaningful marks well-separated in lightness from their ground; a shape that's close in lightness to the background disappears when the piece renders small.
- **Gray on a colored ground looks washed-out and dead** — instead use a darker (or lighter) shade *of that same ground color*.
- Don't rely on color alone to carry meaning (≈8% of men can't separate red/green) — back it with shape, position, or motion.
- The smaller the render, the more contrast and the fewer colors it can hold. An icon at 24px wants two or three committed colors with strong separation, not a subtle six-color gradient scheme.

## Gradients — sparingly, and never on text

A gradient can add depth to a field or a light-through-glass feel, but it's overused as instant "polish." If you use one, keep it a subtle, close-hued shift, not a two-hue rainbow. Never fill display lettering with a gradient for impact — solid color, and let weight and size carry the emphasis (→ [form-and-type.md](form-and-type.md)).

## Quick gate

- [ ] Not one of the banned default palettes.
- [ ] Hue chosen from the subject, not by reflex.
- [ ] Chroma drops toward white/black; shades read as one family.
- [ ] Neutrals faintly tinted toward the hue.
- [ ] One dominant field, one rare accent (60/30/10 by weight).
- [ ] No pure `#000`/`#fff`.
- [ ] Contrast holds at the smallest size it'll render.
