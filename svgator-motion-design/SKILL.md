---
name: svgator-motion-design
description: >
  The craft layer for authoring standalone SVG assets through the SVGator MCP — designing the artwork,
  directing the motion, and wiring the interaction. Turns a prompt ("animate this logo", "make a loading
  spinner", "an icon that reacts on hover") into an art-directed, well-composed piece, then hands off to the
  MCP's tools to build it. Apply whenever you are GENERATING or EDITING a project's design, motion, or
  interactivity. Skip it for pure export, render, or file inspection. Covers icons, logo reveals, loaders,
  illustrations, stickers, explainers, and hero loops — that play on load, loop, or respond to input
  (hover / click / scroll / Player API). NOT for app or framework UI motion (React/CSS component states,
  page transitions) — that's live-app engineering, not an authored SVG asset.
license: MIT
metadata:
  author: SVGator
  version: "3.0.0"
---

# SVGator Motion Design

You are the designer and motion director, not the tweening engine. The job is to decide what the piece looks like, what moves and why it feels right, and how it answers the user if it's interactive — then let the animation carry a bit of story, weight, and life. This skill is the craft layer — taste and direction; the SVGator MCP's tools do the building. It works in three phases: **design the still, direct the motion, wire the interaction.**

**Reach for this when** the deliverable is a self-contained SVG asset — one that plays, loops, *or responds to input*: an animated icon, a logo reveal, a loader, an illustration, a sticker, an explainer beat, a hero loop, a hover-reveal, a click-to-toggle, a scroll-scrubbed sequence. Exported as animated SVG, Lottie, GIF, or video. Interactivity is a property of the *asset*, delivered by SVGator's own triggers and Player API → [director/interactivity.md](director/interactivity.md).

**Reach elsewhere when** the motion *is* a live app's UI behavior — React/framework component states, CSS transitions on app DOM, page-routing transitions. That's app engineering, not an authored SVG asset.

## Inside the SVGator MCP

This is the craft half of the toolset; `describe_shape` and the authoring tools are the mechanics half. They hand off in one direction:

**First, though — does SVGator already have it?** `list_templates` searches a library of finished, professionally animated pieces (loaders, icons, logos, UI elements). Starting from one is not the lesser answer: for a generic brief ("a loading spinner", "an animated download icon") it is usually the better one, and the craft below then goes into *directing the edit* — recolor to the brand, retime, cut what doesn't serve the piece — instead of authoring from zero. A template is read-only, so `duplicate_project` it first; everything below then applies to the copy. Author from scratch when the brief is specific to this user — their logo, their character, their story beat — or when nothing in the library is close.

1. **Design the still** — if you're drawing the artwork (not animating supplied art), get composition, color, and form right first (everything under "Design the still frame first" below). A weak drawing can't be saved by motion.
2. **Decide the motion** — the read, the personality, the one move, the timing (everything below).
3. **Decide the interaction** — if the piece responds to input, choose the trigger and the response alongside the motion → [director/interactivity.md](director/interactivity.md).
4. **Confirm exact shapes** — call `describe_shape` for any element or channel before you write it; never guess field names.
5. **Author it** — `create_project` / `edit_part`, with animators nested by group → channel.
6. **Wire the trigger, if interactive** — interactivity ships at export, not in the project JSON: `export_project` sets `start` (load|hover|click|scroll|programmatic) and the per-event action, or export `programmatic` and drive the Player API. → [reference/interactivity.md](reference/interactivity.md).
7. **Verify** — a populated `settings.animation`, then watch a render, then run the taste pass.

Design first, build second. A technically valid animation with no craft — or motion laid over a generic, badly-composed drawing — is the exact failure this skill exists to prevent.

## Design the still frame first

If you're drawing the artwork — not animating something supplied — the still has to be good before it moves. Motion amplifies a strong composition and equally amplifies a weak one. Run the **AI-slop test** on the frozen frame: *if someone said "an AI made this," would they believe it instantly?* If yes, fix the drawing before you keyframe.

Three things carry the still:
- **Composition** — one clear hero, hierarchy that survives the squint test, generous negative space, off-center balance over the dead-center reflex. → [design/composition.md](design/composition.md)
- **Color** — a committed palette with one rare accent; the brand's real hue, not a default; no cyan-on-dark / purple-blue / neon-glow tells; no pure black or white. → [design/color.md](design/color.md)
- **Form & lettering** — one shape language (corners, stroke weight), quiet tinted depth over generic drop-shadows, non-reflex type set with real hierarchy. → [design/form-and-type.md](design/form-and-type.md)

Skip this phase when the artwork is provided and only motion (or interactivity) is asked for.

## Your instrument — what SVG motion is actually made of

Good motion design starts from knowing your medium's real expressive range. In SVGator, these are the strings you play. Choose the one that *carries the meaning*, not just the one that happens to move.

| The move | What it says | Reach for it when |
|----------|--------------|-------------------|
| `transform.translate` / `scale` / `rotate` | arrival, importance, energy, life | entrances, emphasis, spin, bounce |
| `transform.origin` | *where* a thing pivots and grows from | always set it to the visual center before you scale or rotate |
| `stroke.dashOffset` (+ `dashArray`) | a line drawing itself — handwriting, building, self-assembly | logo strokes, signatures, outlined icons, connectors |
| `shape.path` morph | one thing becoming another | icon-to-icon, liquid blobs, a shape that transforms |
| `fill.paint` / gradient drift | state, mood, warmth, a light moving through | success/error color, ambient atmosphere |
| `compositing.opacity` | presence and absence | fades — but never carrying a moment alone |

Two channels is the sweet spot. One reads as thin; five reads as busy. And a move only lands if its easing has feeling — which SVGator gives you per keyframe, with an unbounded curve you can push past 1 to spring into place with no extra keyframes. That single detail is where a lot of the craft lives → [reference/timing-easing.md](reference/timing-easing.md).

## Name the piece before you touch a keyframe

Each kind of piece has its own clock, its reason to move, and its way to fail. Pin the type and half the decisions settle themselves — how long, loop or land, which channels do the talking, where the craft has to be flawless.

→ **[reference/output-types.md](reference/output-types.md)** — icon, logo reveal, loader, illustration, sticker, explainer, data viz, hero loop: the durations, channels, signature move, and trap for each.

## The read — decide it before you build it

0. **Does the artwork exist, or must I design it?** If you're drawing it, make the still frame good first — composition, color, form (→ "Design the still frame first" above). If it's supplied, skip to step 1.
1. **What is it, really?** One shape or a whole scene? That sets the type above, and the scale of everything after.
2. **What should it make someone feel?** Joy, calm, precision, energy. The feeling picks the easing, the pace, the amplitude — before any channel does. → [director/emotion-mapping.md](director/emotion-mapping.md)
3. **What's its personality?** Playful, Premium, Corporate, Energetic — read it off the artwork and the brand, then hold it consistently. → [director/motion-personality.md](director/motion-personality.md)
4. **What's the tiny story?** Setup → action → resolution, even inside 800ms. Does it land or loop? → [director/narrative-structure.md](director/narrative-structure.md)
5. **What's the one move that carries it?** Pick the channel that means what you're saying, add one to support it. → [reference/property-meaning.md](reference/property-meaning.md)
6. **How is it timed and eased?** Duration from the piece type; a felt curve on every move. → [reference/timing-easing.md](reference/timing-easing.md)
7. **Where's the second and third layer?** One moving thing is a tween, not a design. → below.
8. **Does it respond to input?** If hover/click/scroll/Player API drives it, decide the trigger and the response alongside the motion. → [director/interactivity.md](director/interactivity.md)

> Stuck on step one? [director/decision-framework.md](director/decision-framework.md) walks it from purpose to move.

## The thing that separates design from tweening: layers

A single element sliding in is what everyone's default does. Motion that reads as *designed* moves on three layers at once:

- **Primary** — the one move the eye follows. Full amplitude.
- **Secondary** — the supporting cast that makes it believable: a shadow reacting, a trailing part, an offset stroke. 30–50%, and it arrives 50–150ms *late* — that lag is what sells it.
- **Ambient** — the life underneath: a slow drift, a breath, a gradient shifting. 10–20%, never asking for attention.

A logo mark scales in (primary), its wordmark strokes draw on behind it (secondary), a soft glow breathes under the whole thing (ambient). Miss the second and third layers and it looks cheap — that's the single most common failure. → [director/core-philosophy.md](director/core-philosophy.md)

## Craft laws — break these and it reads as amateur

1. **No linear easing on anything spatial.** Linear is for a continuous spin or a progress fill and nothing else. Every real move gets a curve with feeling.
2. **Opacity never carries a moment alone — and nothing appears from nothing.** Pair every fade with a move or a scale. Start a scale-in at ~0.9, never 0: a shape should already have a body before it moves, or it reads as a glitch popping into existence.
3. **Pivot before you scale or rotate.** Set `transform.origin` at the visual center, or the element swings from its corner.
4. **Always two layers or more.** Primary alone is the tell of a generated animation.
5. **Loops are judged on their worst repeat.** Match the first and last pose so the seam is invisible (or ping-pong it), and leave nothing clipping at the edge when it springs or floats.
6. **The still stands on its own.** If you drew the artwork, it must pass the AI-slop test frozen — before a single keyframe. Motion can't rescue a generic or badly-composed drawing.
7. **An interactive piece acknowledges every input** — and its exit is usually its entrance reversed, not a second animation.

→ Full gate: [reference/quality-checklist.md](reference/quality-checklist.md) · When it moves but looks wrong: [reference/troubleshooting.md](reference/troubleshooting.md)

## Personality at a glance

Pick one and commit — a consistent signature is what makes a set of animations feel like one hand made them.

| | Beats run | Signature curve | Spring (bezier y past 1) |
|--|-----------|-----------------|---------------------------|
| **Playful** | 200–350ms | ease-out-back | ~1.2–1.4 |
| **Premium** | 350–700ms | (0.4, 0, 0.2, 1) | none — clean, no bounce |
| **Corporate** | 200–400ms | (0.2, 0, 0, 1) | ≤ ~1.05, barely there |
| **Energetic** | 100–250ms | ease-out-expo | ~1.4–1.55 |

→ [director/motion-personality.md](director/motion-personality.md) · overshoot budget in [reference/timing-easing.md](reference/timing-easing.md)

## Choreography — when more than one thing moves

- **Lead with the hero.** One element enters first or biggest; the eye needs somewhere to land.
- **Nothing crosses more than a third of the canvas** without a keyframe changing its direction, speed, or arc.
- **With a crowd, only a third moves at once.** Stagger the rest — total stagger under ~500ms so the piece stays snappy.
- **Counter-motion and follow-through** are where scenes come alive: the hero lifts, the shadow drops and softens.

→ [director/choreography.md](director/choreography.md)

## Where the deeper craft lives

**Design** (`design/`) — the still frame, before it moves
- [composition.md](design/composition.md) — hierarchy, the squint test, negative space, asymmetry, optical alignment
- [color.md](design/color.md) — committed palettes, OKLCH thinking, tinted neutrals, the banned AI palettes
- [form-and-type.md](design/form-and-type.md) — shape language, materiality, anti-slop tells, display lettering

**Direction** (`director/`) — the thinking
- [core-philosophy.md](director/core-philosophy.md) — layers, attention, the anti-flat rules
- [decision-framework.md](director/decision-framework.md) — from purpose to the actual move
- [disney-principles.md](director/disney-principles.md) — the twelve, tuned for SVG
- [motion-personality.md](director/motion-personality.md) — the four archetypes + a brand's motion signature
- [emotion-mapping.md](director/emotion-mapping.md) — feeling → motion, and color's role
- [choreography.md](director/choreography.md) — coordinating a cast
- [narrative-structure.md](director/narrative-structure.md) — setup → action → resolution
- [context-adaptation.md](director/context-adaptation.md) — where the piece lives and ships (embed, loop, reduced-motion, export target)
- [interactivity.md](director/interactivity.md) — designing motion that answers to input: affordance, feedback, hover-reveal / toggle / scroll-scrub

**Patterns** (`patterns/`) — the moves, worked out
- [entrance-exit.md](patterns/entrance-exit.md) · [state-feedback.md](patterns/state-feedback.md) · [ambient-continuous.md](patterns/ambient-continuous.md) · [multi-element.md](patterns/multi-element.md) · [signature-effects.md](patterns/signature-effects.md)

**Reference** (`reference/`) — the lookups
- [output-types.md](reference/output-types.md) — the piece-type playbook
- [property-meaning.md](reference/property-meaning.md) — what each channel connotes
- [timing-easing.md](reference/timing-easing.md) — durations, curves, the overshoot trick
- [interactivity.md](reference/interactivity.md) — SVGator triggers, actions, and the Player API: how interactivity ships
- [quality-checklist.md](reference/quality-checklist.md) · [troubleshooting.md](reference/troubleshooting.md)
