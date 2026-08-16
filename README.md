# GenLayer Spinner — "Converging Minds"

Submission for the **Design the GenLayer Spinner** mission.

## Concept

GenLayer's own homepage describes the protocol as "a consensus between many
minds": independent validators, each reasoning on their own, converge on one
answer. The spinner turns that exact mechanic into motion instead of
inventing a generic loading shape:

- **Three static nodes** sit at the vertices of an equilateral triangle —
  the same upward-triangle orientation as the GenLayer mark (Δ). They
  represent the validator set.
- **One arc sweeps the ring** that connects them, continuously, forever —
  the poll that closes into consensus, looping the way a loading state
  should.
- **A faint track ring** (16% opacity) gives the eye the full orbit so the
  arc reads as "in progress" rather than a random spinning line.

Nothing else is added. At 16px the three nodes and the arc are still
distinguishable, which was the hard constraint — most "clever" spinner
concepts fall apart below 24px; this one was designed at 40px and checked
down to 16px from the start.

## Color

Uses the official brand palette from genlayer.com/brand:

- **Kinetic Cobalt** `#110FFF` — the arc and nodes. It's saturated enough to
  read on both Photon (`#FFFFFF`) and Carbon Void (`#070707`) backgrounds
  without needing a separate light/dark asset.
- The track ring is Kinetic Cobalt at low opacity rather than a separate
  gray, so the whole mark stays one hue — quieter, and it never clashes with
  whatever accent color a given Portal page is using elsewhere.

## Files

- **`genlayer-spinner.svg`** — the primary deliverable. Self-contained SVG
  using SMIL (`<animateTransform>`), so it animates as a plain
  `<img src="genlayer-spinner.svg">` with no CSS or JS required — drop it
  into any loading state in the Portal as-is.
- **`genlayer-spinner.css`** + **`spinner-inline-snippet.html`** — an
  alternate CSS-animation version for contexts that embed the SVG inline in
  the DOM and want to theme it via `--gl-spinner-color`, or resize by
  overriding `width`/`height` on `.gl-spinner`. Respects
  `prefers-reduced-motion` by slowing to a gentle opacity pulse rather than
  freezing outright (a static spinner reads as "stuck", not "loading").
- **`demo.html`** — open in a browser to see the spinner on light and dark
  backgrounds at 64px / 32px / 16px side by side.

## Usage

```html
<!-- simplest — works anywhere, no setup -->
<img src="genlayer-spinner.svg" width="24" height="24" alt="Loading" />
```

```html
<!-- inline, themeable via CSS -->
<link rel="stylesheet" href="genlayer-spinner.css" />
<svg class="gl-spinner" viewBox="0 0 40 40" role="img" aria-label="Loading">
  <circle class="gl-spinner__track" cx="20" cy="20" r="15" />
  <circle class="gl-spinner__node" cx="20" cy="5" r="2.3" />
  <circle class="gl-spinner__node" cx="32.99" cy="27.5" r="2.3" />
  <circle class="gl-spinner__node" cx="7.01" cy="27.5" r="2.3" />
  <circle class="gl-spinner__arc" cx="20" cy="20" r="15" />
</svg>
```
