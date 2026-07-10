# Interactivity — Motion That Answers

Most SVG animations *play*. An interactive one *answers* — the user's action is the story, and the motion has to acknowledge it. That shifts the craft: the response must feel earned, land instantly, and survive being interrupted.

## Two questions before you make anything interactive

1. **Should it be?** If it reads fine playing on load or looping, interactivity only adds cost and a discovery problem. Reach for it when the user's action *is* the point — a toggle, a reveal-on-demand, a timeline they scrub. Don't gate delight behind a click. And let *frequency* set the amplitude — the more often the user triggers it, the more instant and subtle the response should be:

   | How often the user triggers it | Response |
   |---|---|
   | Constantly (a state they cross dozens of times) | Near-instant and subtle, or nothing |
   | Occasionally (a click to reveal, a toggle) | Standard interaction motion |
   | Rarely / once (a celebration, a success) | Room to delight |

2. **Will they find it?** Interactivity nobody discovers is worse than none. The resting state has to *invite* the input.

## Affordance — the resting state must promise the response
- A hover-reveal needs a hint at rest (a peek of the thing, a soft idle tell) so the hover feels like *waking it up*, not a surprise.
- A toggle needs two clearly distinct states — the "off" pose has to read as "there's an on."
- If nothing about the still frame says *touch me*, add the smallest thing that does.

## Name the purpose, then acknowledge the input
Every interactive response needs a reason — **feedback** (confirm the input landed), **state** (show what changed), **spatial consistency** (leaves the way it arrived), or **explanation**. "Looks cool" is not a reason for something seen often. And whatever the reason, the element must *visibly react the instant it's touched* — a control that sits dead on press reads as broken, even when it works. The reaction can be tiny; it cannot be absent.

## Feedback timing — interactive motion is FASTER
The user is *waiting* on this one. A response slower than ~100ms feels broken. Interactive beats run quicker than autoplay beats — trim the duration, lead with an ease-out so movement starts on the first frame, and **never ease-in** (it delays the first frame, the exact moment the user is watching). Autoplay can luxuriate; interaction cannot. → [../reference/timing-easing.md](../reference/timing-easing.md)

| Response | Duration |
|---|---|
| Press / tap acknowledgement | 100–160ms |
| Hover reveal, small pop | 125–200ms |
| Click-triggered change | 150–250ms |
| A rare, expressive moment | can run longer |

**Anchor the origin where the user acted.** A response that grows from the point that was touched feels connected; the same move from canvas center feels detached. Set `transform.origin` at the element's own center, or the point of the interaction.

## One timeline, shaped as a forward action

The move that makes interactivity simple: **a piece is ONE timeline, and you author it as the *forward action*** — the thing arriving, opening, activating, filling. You do not author a second animation for the way back. The trigger's *return behavior* reshapes that one timeline into a complete interaction:

| Return | What it does | Use it for |
|---|---|---|
| **reverse** | rewinds the timeline — the exit is the entrance played backward | hover-in/out, toggles: leaves exactly the way it arrived (spatial consistency for free) |
| **freeze** | stops and holds at the current pose | hold-to-commit, a state that should stay put |
| **restart** | replays from the top | a fire-once burst (confetti, celebration) |
| **reset** | jumps back to the start pose | a hard return with no outro |

So a play-in / play-out interaction needs **only the forward timeline** — reverse supplies the exit. The design consequence: **make the forward read correctly played backward**, since that literally *is* the return. Avoid one-way moves that only make sense forward (a letter that unwrites into gibberish, a fill that drains from the wrong edge).

**The hard limit: one timeline per piece.** The return behaviors reshape a single motion — they can't supply a genuinely *different* one. If the brief needs, say, a drumroll on mouse-over and a distinct disappointed slump on mouse-out (two separate motions, not one reversed), that's beyond one timeline. Two honest options: **rescope to the model** (can the second motion be the reverse / freeze / restart of the first? usually yes), or **hand off to SVGator's editor Interactivity panel**, which supports multiple states and separate per-event timelines. Note it — don't fake it with the MCP.

→ How each return maps to an export trigger (`start` + hover/click action) and to Player-API calls: [../reference/interactivity.md](../reference/interactivity.md).

## The interaction patterns

Each of these is one forward timeline plus a return, per the model above:

| Pattern | The feel | Design for |
|---|---|---|
| **Hover-reveal / hover-play** | wake it on hover, settle on leave | quick in, graceful out (exit ~70% of enter); a resting hint. Return = **reverse** |
| **Click-toggle** | two states, one flips to the other | distinct poses; the *reverse* of the "on" motion **is** the "off" — reuse it. Return = **reverse** |
| **Click-fire** | one-shot burst on each click | a self-contained beat that reads from its start pose. Return = **restart** |
| **Scroll-scrub** | the user drives the timeline | readable at ANY frame, monotonic progress, no easing they can outrun |
| **Press & hold** | hold to charge/fill, release to act | a build that reads mid-way; a clear release payoff. Return = **freeze** |

## Reversibility & interruptibility — the real difference
Autoplay runs start to finish. Interactive motion gets *interrupted*: hovered out mid-play, clicked again mid-toggle, scrolled back. Design states you can enter and leave from any point — favour **reverse** and **seek-to-current** over **restart**, so an interrupted move smoothly turns around instead of snapping to zero. A toggle that only works from its resting pose feels broken the first time someone double-clicks it.

## When NOT to
Decorative loops, brand reveals, ambient life — anything whose job is to be *seen*, not *used*. Leave it playing.

> How SVGator actually delivers this — triggers, actions, the Player API, and the honest MCP boundary: [../reference/interactivity.md](../reference/interactivity.md). Two-state design also draws on [../patterns/state-feedback.md](../patterns/state-feedback.md).
