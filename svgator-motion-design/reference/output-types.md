# The Piece-Type Playbook

Before you decide on a single keyframe, name what you're making. A loader is not a logo reveal is not a sticker — each has its own clock, its own reason to move, and its own way to fail. Pin the type first; it settles half your decisions (how long, loop or land, which channels do the talking, where the craft has to be flawless).

These are starting instincts, not rules. Emotion, personality, and the brand override them.

## Read the type in one line

| You're making… | Runs for | Loop or land? | The channels that carry it | The one move that defines it |
|----------------|----------|---------------|-----------------------------|------------------------------|
| **Animated icon** (micro) | 300–800ms | usually lands; a whisper of loop is fine | `scale`, `rotate`, a small `shape.path` | one legible idea — a bell tips, a heart beats |
| **Status icon** (living) | 1–2s | loops forever | `rotate`, `compositing.opacity`, `stroke.dashOffset` | a calm heartbeat you can watch all day |
| **Logo reveal** | 1.2–2.5s | lands, holds | `stroke.dashOffset` draw-on, `scale`, `opacity`, staggered parts | assembly, then a settle — never a single fade |
| **Loader / spinner** | 0.8–1.5s per cycle | loops forever | `rotate` (linear), `stroke.dashOffset`/`dashArray`, `shape.path` | hypnotic, seamless, perfect on the 100th pass |
| **Illustration / scene** | 2–5s | either | everything, staggered, layered | a hero beat with the world reacting around it |
| **Sticker / emoji** | 0.6–1.5s | loops forever | `scale` (squash-stretch), `rotate` (wobble), `translate` (hop) | exaggeration — the one place to push too far |
| **Explainer beat** | 1.5–4s | lands | `translate`, `stroke.dashOffset`, `opacity`, sequenced | a directional read — this, then this, then this |
| **Data viz** (bars/lines) | 0.8–2s | lands | `scale.y` / `shape.size`, `translate`, a wave stagger | growth from a baseline, never a pop from nowhere |
| **Hero / ambient loop** | 3–8s | loops forever | slow `translate`, gradient `fill.paint` drift, `scale` breathe | atmosphere — motion you feel before you notice |

## Loop or land — decide it early, it changes everything

- **Loops** (infinite): loaders, status icons, stickers, ambient/hero — anything embedded as a living accent. The first and last pose must be the same pose, or the seam will flinch every cycle. When a true match is impossible, ping-pong it (`alternate`) instead of forcing it.
- **Lands** (plays once, holds the end): logo reveals, entrances, celebrations, explainer beats. Arrive somewhere resolved and stay there. A one-shot that ends mid-motion reads as broken.

The loop is judged on its worst repetition; the one-shot is judged on its final frame. Design for the one that's actually being watched.

## Give the motion room

Size the canvas to the artwork's real bounds, then leave headroom for whatever springs, floats, or overshoots. A bounce that scales to 1.1 or a drift of 10px needs somewhere to go — clip it at the edge and the whole piece reads as a mistake. Icons and loaders sit happily in a square; illustrations take the art's own aspect. The coordinate space is what matters, not the export resolution — you can up-res later.

## Where each type earns its keep — and where it fails

**Animated icon.** One idea, two channels, done. A notification bell = a `rotate` wobble with a tiny `translate` shake; a heart = a `scale` beat. The failure mode is greed: three ideas crammed into 400ms reads as noise. If you can't name the single thing it's doing, it's doing too much.

**Status icon.** It's on screen constantly, so it has to be watchable, not attention-grabbing. Low amplitude, gentle sine, a slow pulse or orbit. Anything punchy becomes a nag by the tenth loop.

**Logo reveal.** Never a plain fade — that's the default nobody remembers. Layer it: the mark draws or scales in, the wordmark staggers behind it, one ambient touch lands last (a shadow settling, a shine sweeping through). Premium brands earn it with restraint — no overshoot, a slow curve, a generous held pause at the end. See [../director/narrative-structure.md](../director/narrative-structure.md).

**Loader.** The hardest thing to get right, because it's judged on its 100th cycle, not its first. Seamless seam, small amplitude, hypnotic rather than loud. Linear belongs only to a pure rotation; give a dash-chase or a morphing loader eased segments so it breathes instead of ticking. And lean quick — a faster-spinning loader makes the whole piece *feel* faster to the viewer, even when nothing else changed.

**Illustration / scene.** Left unchecked it becomes chaos. Pick a hero, let everything else play secondary or ambient, and hold the 1/3 rule — no more than about a third of the elements moving at once. Stagger the rest. See [../director/choreography.md](../director/choreography.md).

**Sticker.** The one brief where "too much" is the brief. Squash and stretch, overshoot past 1.4, wobble on the way out. Anticipation and follow-through do the heavy lifting; play it safe and it stops being a sticker.

**Data viz.** Numbers should grow, not appear. Bars rise from their baseline (`scale.y` about the bottom edge, or `shape.size`), lines draw on. A wave stagger across the series makes the data feel alive; a synchronized pop makes it feel fake.

**Hero / ambient.** Success is when someone feels the motion before they consciously see it. Slow everything down, keep amplitude tiny, layer a couple of loops at durations that never sync (4s / 5.5s / 3.5s) so the pattern never repeats to the eye.
