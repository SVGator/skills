# Interactivity — Delivery (SVGator triggers + Player API)

SVGator ships interactivity two ways: **built-in triggers** set at export (no code) and the **Player API** (JS control). Design the motion in [../director/interactivity.md](../director/interactivity.md); this is how it actually runs.

## A. Built-in triggers — set at export, no code

Configured on export (SVG format). The **whole animation** responds to the chosen trigger.

| Setting | Values | Notes |
|---|---|---|
| **start** | `load` · `hover` · `click` · `scroll` · `programmatic` | when the animation begins. `css` type supports only `load` / `hover` |
| **hover action** | `freeze` · `reset` · `reverse` · `none` | what hover does (with `start:hover`) |
| **click action** | `freeze` · `restart` · `reverse` · `none` | what click does (needs `type:js` + `start:click`) |
| **scroll** | offset `1`–`100` | fires start at a scroll position (needs `type:js` + `start:scroll`) |

Design → trigger:
- **Hover-reveal** → `start:hover`, action `reverse` (plays in on enter, back out on leave) or `reset`.
- **Click-toggle** → `start:click`, action `reverse` (each click flips direction) or `freeze`.
- **Scroll-triggered** → `start:scroll` with an offset (fires as it scrolls into view).

These are **whole-animation** triggers — one timeline, one response. For scrubbing, multiple states, or wiring to app logic, use the Player API.

## B. Player API — programmatic JS control

Export **SVG · type `js` · start `programmatic`**, then drive it from your page. The player is attached to the exported `<svg>` root element as **`.svgatorPlayer`**.

```js
// Inline SVG — use the exported <svg>'s own id:
const el = document.getElementById('e5478wvxh25l1');
el.svgatorPlayer.ready(p => p.play());

// Embedded via <object> (same-domain, served over http — NOT file://):
const obj = document.getElementById('animated-svg');
const doc = obj.contentDocument || obj.contentWindow.document;
doc.getElementById('e5478wvxh25l1')?.svgatorPlayer?.ready(p => p.play());
```

**Methods** (each returns the player, so they chain):
`play()` · `pause()` · `stop()` (reset to first frame) · `restart()` · `reverse()` · `toggle()` / `togglePlay()` · `seek(percent 0–100)` · `seekTo(ms)` · `seekBy(ms, ±)` · `set(prop, value)` · `ready(cb)` · `destruct()`

**Settable via `set(prop, value)`:** `direction` (−1 | 1) · `fill` (−1 | 1) · `alternate` (bool) · `iterations` (0–∞, 0 = infinite) · `speed` (0–100, 1 = 100%) · `fps` (1–100)

**Events** — `on(name, fn, prepend)` / `off(name, fn)`:
`play` · `pause` · `restart` · `reverse` · `stop` · `end` · `keyframe` (fires per frame with the offset in ms).

Craft pattern → wiring:

| Pattern | JS |
|---|---|
| Hover-reveal | `mouseenter → play()`, `mouseleave → reverse()` |
| Click-toggle | `click → toggle()` (or `reverse()` for a two-way flip) |
| Scroll-scrub | scroll handler → `seek(progressPercent)` — the user drives the timeline frame-for-frame |
| Press & hold | `mousedown → play()`, `mouseup → pause()` (or `seekTo` a charge level) |
| Sync to app state | `set('speed', …)`, `set('direction', …)`, `on('end', …)` to chain the next beat |

## The honest MCP boundary
Through the SVGator MCP you deliver interactivity by **exporting with the right trigger** (`start` / `hover` / `click` / `scroll`), or by **exporting `programmatic` and writing the driving JS yourself** — the Player API runs in *your* page, not inside the project. What the MCP data model does **not** author is **per-element event binding** ("click element A → animate element B"): that's a SVGator editor (Interactivity panel) feature and isn't in `describe_shape`. So — whole-animation triggers and Player-API control, yes; element-to-element interactivity, editor-only.
