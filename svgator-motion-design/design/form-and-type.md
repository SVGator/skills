# Form, materiality & lettering — the details that read as designed

Composition sets where things go; color sets the mood. This is the level of the marks themselves — the quality of the shapes, how they're finished, and any lettering — plus the anti-slop pass that keeps the piece from looking machine-made. It's the last gate on the still before motion.

## Shape language — pick one and hold it

A set of marks reads as one hand only if they share a vocabulary. Decide these once and apply them everywhere in the piece:

- **Corner radius** — sharp, softly rounded, or fully round. One radius family, not a mix of crisp and pillowy corners in the same mark.
- **Stroke weight** — a single stroke width across an icon (or a deliberate two-weight system), never a random assortment. Inconsistent stroke weight is the fastest way an icon set looks amateur.
- **Terminals & joins** — round vs butt caps, mitred vs rounded joins: pick and keep.
- **Geometry vs organics** — a piece is built from circles-and-straights *or* from hand-drawn curves. Mixing the two languages without reason looks like a collage of two designs.

Consistency here is what lets the motion layer stay legible — the eye already understands the system, so it can follow the movement.

## Materiality — depth without the tells

Depth should be quiet. The generated-design reflex is a soft gray drop-shadow under a rounded rectangle, and it's forgettable.

- **Tint shadows toward the background hue** and keep them subtle — if you clearly *see* the shadow, it's too strong. A shadow is a hint of elevation, not a hard edge.
- Prefer honest structure — overlap, scale, a real cast direction — over a default blur under everything.
- In a dark piece, depth comes from *lighter* surfaces stepping forward, not from shadow.

## Anti-slop — the tells to refuse on sight

These patterns scream "machine output." If you're about to draw one, rebuild the element differently.

| Tell | Why it reads as generic | Instead |
|------|------------------------|---------|
| Rounded rectangle + generic gray drop-shadow | The single most templated shape there is | Earn depth through structure and a tinted, subtle shadow — or none |
| Gradient-filled text | Decorative, meaningless, top-tier tell | Solid color; emphasize with weight/size |
| Glassmorphism everywhere (blur + glow borders) | Effect used as a substitute for design | Use frosting only where a real glass metaphor exists |
| Colored side-stripe accent bar on a block | Never looks intentional at any width/color | A full outline, a tint, a leading glyph, or nothing |
| Neon outer glow on dark | "Cool" without a decision behind it | A tinted, contained highlight; commit to a palette instead |
| Oversaturated accent with no neutral rest | Nothing to make the accent feel rare | Desaturate slightly; give it a neutral field (→ [color.md](color.md)) |

## The AI-slop test

Hold the frozen frame up and ask: *if I said "an AI made this," would someone believe me instantly?* If yes, that's the problem. A distinctive piece makes people ask "how was this made?" — not "which model made this?" Run this test on the still **before** animating, because motion can't cure a generic drawing.

## Lettering & type — for marks, not paragraphs

Type in an SVG asset is display lettering — a wordmark, a logo line, a short label — not body copy. Note the medium constraint: **text in an SVGator asset is essentially static, and for reliable export it's typically outlined to paths**, so treat lettering as *shapes with typographic taste*, and confirm the font is embedded or converted before export.

Within that:

- **Reject the reflex fonts.** The trained defaults create monoculture — Inter, Roboto, Open Sans, and the "tasteful" go-to display serifs everyone reaches for. Pick a face whose physical character fits *this* brand (a hand-painted sign, a terminal manual, a museum caption), not the category cliché. "Elegant" doesn't automatically mean a serif; "technical" doesn't automatically mean a mono; "modern" doesn't mean the geometric sans everyone uses.
- **Don't use monospace as lazy shorthand** for "technical/developer."
- **Fewer sizes, more contrast.** Hierarchy from a clear jump in size *and* weight (aim ≥1.25× between steps), not from five sizes a hair apart.
- **All-caps only for short labels**, never for a whole phrase — set long text sentence-case.
- **Track display lettering tighter**; large type set at default spacing looks loose and unset.
- Usually **one type family in a couple of weights** beats two competing faces. Add a second only for genuine contrast (a display line + a small supporting label).

## Final still-frame gate

Before any keyframe:

- [ ] One shape language — corners, stroke weight, joins, geometry all consistent.
- [ ] Depth is quiet and tinted; no default gray drop-shadow reflex.
- [ ] No anti-slop tells (gradient text, glow, side-stripe, glass-everywhere).
- [ ] Lettering uses a non-reflex face, real hierarchy, tracked; font embedded/outlined.
- [ ] The AI-slop test passes.

A still that clears this — plus [composition.md](composition.md) and [color.md](color.md) — is worth animating. Now direct the motion.
