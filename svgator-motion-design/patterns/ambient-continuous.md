# Ambient & Continuous Patterns

The living-accent layer of a loop. Ambient motion never competes for attention — amplitude 10–20% of any primary motion. It keeps a piece breathing on the 100th loop without ever demanding a look. Everything here loops seamlessly: last pose = first pose.

Easing in CSS notation; named-curve → value in [../reference/timing-easing.md](../reference/timing-easing.md). Ambient wants **sine** (0.37, 0, 0.63, 1) or **linear**, never a sharp curve.

## Breathing / Pulse

- `transform.scale` oscillation 0.98–1.02, sine, 2000–4000ms/cycle
- Alt: `compositing.opacity` 0.7 → 1.0
- Set `transform.origin` to center so it breathes evenly

| Context | Scale range | Duration | Opacity range |
|---------|-----------|----------|--------------|
| Active indicator | 0.95–1.05 | 2000ms | 0.6–1.0 |
| Idle / waiting | 0.98–1.02 | 3000ms | 0.8–1.0 |
| Background element | 0.99–1.01 | 4000ms | 0.9–1.0 |
| Attention accent | 0.97–1.03 | 2500ms | 0.7–1.0 |

Past ±5% scale it stops being ambient and starts demanding attention.

## Floating / Drift

- `transform.translate` Y ±5–15px, sine, 3000–5000ms/cycle
- Optional slight `transform.rotate` ±2–3°, phase-offset 30% from the position cycle

**Layered floating** — give each element a different duration so they never sync:
- Element 1: 4000ms, ±10px
- Element 2: 5500ms, ±8px (offset 30%)
- Element 3: 3500ms, ±12px (offset 60%)

## Continuous Rotation

- Spinners / processing: **linear** `transform.rotate`, 800–2000ms/rev
- Decorative: much slower

| Variant | Speed | Use |
|---------|-------|-----|
| Slow spin | 10–30s/rev | Background decoration, halos |
| Gear-like | 3–5s/rev | Technical / mechanical marks |
| Orbital | 5–15s/rev | Space / science themes |
| Wobble | 2–4s/cycle, sine | Playful idle sway |

## Shimmer / Gleam Sweep

- Gradient highlight sweeps left → right across a shape, 1500–2500ms/sweep
- Pause 2000–5000ms between sweeps so it feels occasional, not strobing
- Opacity gradient 0% → 30% → 0%
- Use for: metallic/premium accents, "new" badges, glass surfaces, subtle skeleton life

## Gradient Shift

- Slowly move `fill.paint` gradient position or rotate its angle
- 8000–20000ms/cycle; range ±10–20% position or ±15° angle
- Linear or sine; must be imperceptible at a glance — you feel it, you don't watch it

## Particle Ambient

Fewer, larger particles read better and export lighter than a dense swarm.

| Type | Count | Motion | Size | Opacity |
|------|-------|--------|------|---------|
| Snow / falling | 10–20 | 20–60px/s down, ±10–20px drift | 3–8px | 30–70% |
| Dust / motes | 5–10 | 10–30px/s mixed | 2–5px | 20–50% |
| Sparkle / stars | 8–15 | opacity pulse 0→100%→0, 500–1500ms each, random stagger | small | — |

Keep it to transform + opacity. Cap total ambient elements so the file stays light.

## Depth (Layered-Loop Parallax)

Not scroll- or mouse-driven — just layers drifting at different speeds to fake depth inside a loop.

| Layer | Drift speed | Content |
|-------|------------|---------|
| Foreground | Fastest, largest amplitude | Hero shapes |
| Midground | Medium | Decorative cards, mid shapes |
| Background | Slow | Patterns, scenery |
| Deep background | Slowest, smallest | Texture, atmosphere |

Offset each layer's phase and duration so the parallax reads as continuous depth, never as a synced slide.

## Combining Ambient Layers

| Layer | Type | Example |
|-------|------|---------|
| Background | Gradient shift or depth drift | Slow color-temperature change |
| Midground | Floating or particles | Gentle drifting shapes |
| Foreground | Breathing or shimmer | Subtle pulse / gleam on the hero |

Total ambient energy: max ~20% of the primary motion's. See the three-layer model in [../director/core-philosophy.md](../director/core-philosophy.md).
