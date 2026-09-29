# Signature Effects

The standout moves — each one a recognizable "how did they do that." Reach for one when a piece needs a hook beyond a clean entrance. **One signature per piece**; two competing tricks read as a demo reel, not a design.

Everything here is built only from what SVGator can actually animate — transform, opacity, stroke dash, path morph, gradient paint, and filters. Nothing that needs a live DOM or scripting.

## Self-drawing line art
The flagship. A stroke reveals itself as if a hand were drawing it — `stroke.dashOffset` from the full path length down to 0. Nothing else says *being made* like it. Set `dashArray` to at least the path length; fill fades in after the outline lands. Signatures, outlined logos, connectors, monoline icons. → also [entrance-exit.md](entrance-exit.md).

## Gradient gleam / sweep
A band of light travels across a shape — shine on metal, a "new" badge catching the eye. Built by animating the `fill.paint` (or `stroke.paint`) linear-gradient's `from`/`to` positions across the shape, or a bright stop sliding through the stops. Keep the stop **count matched** across keyframes, exactly like a path morph, or the gradient jumps instead of gliding. *Trap:* subtle is premium; a fast rainbow is a toy.

## Shimmer / skeleton sweep
The looping, low-contrast cousin of the gleam — a soft highlight passes left-to-right on a cycle, paused 1–2s between passes. Same gradient-position technique, kept faint. Premium accents, loading placeholders. → [ambient-continuous.md](ambient-continuous.md).

## Glitch / RGB-shift
A mark tears into its color channels for a few frames. Duplicate the shape in two or three copies tinted toward red / cyan, set a `screen` or `lighten` blend (`compositing.blend`), and jitter their `transform.translate` while flicking `compositing.opacity`; a pulse on the `hue-rotate` filter deepens it. *Trap:* brief and rare — 200–400ms bursts, never sustained, or it reads as broken rather than styled.

## Particle burst
The punctuation on a win — a cluster of small shapes scales and translates outward while fading, staggered from a center point (`transform.scale` + `translate` + `compositing.opacity`, staggered start times). *Trap:* match the energy to personality — confetti on a fintech mark is wrong; a lone glow ring on a kids' app is flat. → [state-feedback.md](state-feedback.md).

## Mesh / blob drift
An organic, lava-lamp ground: soft color blobs drifting and merging. Built from a few large ellipses with a heavy `blur` filter, slow looping `translate`/`scale`, and gradient fills. (Not a true SVG mesh gradient — the *look*, made from blurred blobs.) Ambient only, slow and low-contrast. *Trap:* the blur **is** the effect — without it you just have hard-edged ovals sliding around.

## Kinetic marquee
An endless band of text or shapes scrolling sideways forever. Duplicate the band end-to-end, then animate the group's `transform.translate.x` from 0 to −(one band width), **linear**, on a loop. *Trap:* the duplicate has to be seamless or the loop jumps at the reset; any easing other than linear makes the scroll visibly pulse.

## Rotating badge / lockup
A circular seal or ring of text turning slowly — `transform.rotate` on the pre-arranged circular artwork, linear, or a gentle ease-in-out for a "catch" that reads more alive than dead-constant. Pair it with a still center so the eye has an anchor. *Note:* SVGator can't lay a live text string onto a path — the text has to already be arranged as vectors (converted to outlines or drawn in a circle); then it simply spins.

## What SVGator can't do — and the honest workaround
- **Text scramble / decode** (Matrix-style glyph cycling): **not possible.** A text element's content is static — you can't keyframe the characters. Nor can you animate *part* of a string: the per-run styling in `shape.rangeStyles` is static, and the runs aren't elements, so they have no animators of their own. To reveal letters one at a time, each letter has to be its own `text` element, which you then stagger like any other group. Otherwise approximate the *feeling*: animate the whole text's opacity or position, or convert it to outlines and draw it on with `stroke.dashOffset`.
- **Anything that reacts to the cursor, scroll, or a click** (magnetic pull, hover trails, spotlight borders): out of scope by definition — these pieces play on their own. If the brief needs reactive motion, it's a different tool.
