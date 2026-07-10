# Feedback Moment Patterns

Self-contained beats that *depict* a state — success, error, loading — and play on their own. Nobody clicks to trigger them; the piece is authored to run on load or loop. Think of the checkmark animation itself, not the button that would fire it.

Easing in CSS notation; named-curve → value in [../reference/timing-easing.md](../reference/timing-easing.md).

## Success / Celebration Moments

### Checkmark Draw + Pop + Burst
1. Container pops: scale 0.9 → 1.0 (200ms, back easing (0.34,1.4,0.2,1), 5–10% overshoot)
2. Check draws on: `stroke.dashOffset` full → 0 (150ms, ease-out, ~100ms in)
3. Color resolves to green (`fill.paint`/`stroke.paint`, 200ms)
4. Burst: radiating particles/rays scale out + fade (300ms) as the ambient beat
5. Total 400–500ms; settle to a calm held pose

| Personality | Container overshoot | Burst | Feel |
|------------|--------------------|-------|------|
| Playful | 10–15% | Confetti, many particles | Joyful |
| Premium | 0–5% | Single soft glow ring | Refined |
| Corporate | 0–3% | Minimal or none | Clean |
| Energetic | 15–20% | Fast radial rays | Punchy |

### Confirmation Badge
1. Badge scales from 0 → 100% (200ms, back easing)
2. Inner mark (check/star) draws or scales in (150ms, ~50ms later)
3. Background pulse breathes once (300ms, sine)

### Payment / Task Complete
1. Spinner cross-dissolves into a checkmark (opacity swap, 200ms)
2. Check draws (dashOffset, 200ms); container shifts to success color (200ms)
3. Label fades + rises in (translate + opacity, 200ms, ~100ms delay)
4. Optional confetti burst (300–500ms)

## Error / Alert Flourishes

### Shake + Color Flash
- Horizontal `transform.translate` oscillation ±10–15px, 2–3 cycles of decreasing amplitude
- ease-in-out, 300–400ms total; settles exactly at origin (no overshoot)
- `fill.paint`/`stroke.paint` flashes to red simultaneously, then holds or eases back

### Alert Icon Beat
1. Icon scales in fast (150ms, slight overshoot for energetic, none for corporate)
2. Color snaps to red/amber
3. One sharp shake (±8px, 200ms)
4. Optional slow pulse afterward (2–3s, sine) to keep the alert "live"

### Warning Pulse
1. Amber outline draws or fades in (150ms)
2. Warning glyph scales in with subtle overshoot (150ms)
3. Continuous gentle pulse (scale 0.98–1.02, 2–3s/cycle, sine) so it reads as ongoing caution

## Loading Loops

All loop seamlessly — the last pose must equal the first. Keep amplitude modest; these are seen repeatedly.

### Spinner
- Continuous `transform.rotate` 0 → 360°, **linear**, 800–1500ms/rev
- Optional breathing pulse layered underneath (scale 0.98–1.02, 2–3s, sine)

### Dash-Chase
- `stroke.dashOffset` cycles continuously around a ring/path, linear, 1000–1500ms/loop
- Reads as a segment chasing its own tail; pair a short `stroke.dashArray` gap for a comet look

### Morphing Dots
- 3+ dots pulse scale in staggered sequence (each 0.6 → 1.0 → 0.6), stagger 120–160ms, sine
- Or dots translate in a wave; total cycle 1000–1400ms
- Reads as "thinking" — indeterminate, never frantic

### Skeleton Shimmer
- Gradient sweep left → right across placeholder shapes, 1500–2000ms/sweep
- Opacity gradient 0% → 30% → 0%; base fill 10–20% opacity
- Optional pause 1000–2000ms between sweeps

### Indeterminate Bar
- A segment oscillates position/width along a track, 1500–2500ms, ease-in-out
- Continuous; smooth, never jittery

## Rules

- **Never opacity alone for a moment.** A success or error beat needs scale or position doing the work; opacity only supports. (See [../reference/property-meaning.md](../reference/property-meaning.md).)
- **Error settles at origin.** A shake that ends off-center reads as broken, not alarmed.
- **Loops need a seam and a breath.** Match start/end pose; leave a beat of stillness before the cycle repeats.
- **Match burst energy to personality.** Confetti on a fintech success mark is wrong; a lone glow ring on a kids' app is flat.
- **A crossfade that shows two overlapping states → blur the swap.** When one state dissolves into another (spinner → checkmark, icon A → B) and you can see both at once, a brief `blur` filter (~2px) on both during the transition blends them into a single read instead of two shapes ghosting over each other.
