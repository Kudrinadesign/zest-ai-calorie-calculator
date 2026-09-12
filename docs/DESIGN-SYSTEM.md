# Zest design system

Every screen in the Figma file is assembled from the components below, and every colour,
size, gap, radius, stroke, blur, opacity and type setting on them comes from a variable or a
style bound to variables. Pages `03 · Components` (overview) and `03.1`–`03.7` (one page per
family) document each component with its states, tokens and usage.

## Tokens — 5 collections, 354 variables

| Collection | Modes | Variables | What lives there |
|---|---|---|---|
| **Primitives** | Value | 78 | Raw colours (sand, plum, wine, ember, butter, ink, night, indigo, saffron, tomato, clay, peach, white) incl. exact alpha steps. Hidden from pickers (no scopes). |
| **Zest · Natural** (semantic) | Default | 210 | Colour roles aliased to primitives — `ground/*`, `bloom/*`, `ink/*`, `onbloom/*`, `onphoto/*`, `surface/*`, `glass/*`, `action/*`, `accent/*`, `macro/*`, `line/*`, `scrim/*`, `fade/*`, `glow/*`, `ai/*`, `icon/*`, `system/*` — and `space/*` (2–72), `size/*` (controls, icons, tiles, ring, lens…), `radius/*`, `stroke/*`, `blur/*`, `opacity/*`, `shadow/*`. |
| **Typography** | Value | 38 | `type/family`, `type/weight/*`, `type/size/*`, `type/line/*`, `type/tracking/*`. Every text style is bound to these. |
| **Prototype · Day** | Before breakfast · Breakfast added · After · Dinner planned | 15 | The state of the day: kcal left, macros, bar rests, Zest's message, Budget card state, snackbar visibility. |
| **Prototype · Recipe** | Original · Adjusted | 13 | Recipe detail before/after *Apply adjustment*. |

Every variable has an explicit scope and WEB (`var(--…)`) + iOS code syntax. The five boolean
prototype variables can't carry scopes — a Figma limitation.

**Styles.**
- **16 text styles:** Head/XL·L·M, Text/Title·Body·S·Label·Caption·Action·Micro, Metric/XL·L·S, System/Status, Brand/Wordmark (+ L). Family, weight, size, line height and tracking are all bound to `type/*`.
- **8 effect styles:** Glass/Control·Tile·Sheet·Deep, Bloom/Soft, Shadow/Float, Shadow/Text on photo, Glow/AI. Blur radius, shadow colour, offset and spread are bound to `blur/*`, `shadow/*` and `glow/*`.

## Components — 64, by family

| Page | Components (variants) |
|---|---|
| 03.1 Icons | 39 Lucide icons (ISC) on a 24 px grid; stroke `stroke/icon`, colour `icon/*`. Used through an instance-swap property everywhere. |
| 03.2 Actions | **Button** (24: Primary/Secondary × Large/Medium/Small × Default/Pressed/Disabled/Loading) · **Ghost button** (18: Brand/Accent/Ink/Danger/On photo/Highlight × 3 states) · **Icon button** (26: Light/Tinted/Filled/Glass × Regular/Small × Default/Pressed/Selected/Disabled) · **Chip** (9: Filter/Suggestion × Selected × states) · **Capture control** (Shutter/Library × 3) |
| 03.3 Inputs & selection | Toggle (4) · Radio (4) · Step indicator (3) · Segment (6) + Segmented control (2) · Stepper (2) · **Search field** (5: Empty/Focused/Filled/Error/Disabled, leading + trailing icon) · Composer (3) |
| 03.4 Navigation | Status bar (2) · **Nav bar** (leading icon · title · trailing icon; On photo/On bloom) · Tab item (12) + **Tab bar** (5) · **Day** (4) + Week strip · **Calendar day** (5) |
| 03.5 Data display | Macro bar (10: 5 macros × Solid/Added) · Macro stat (12: Card/Inline/Compact/What-if × 3) · Tag (3) · Bullet (2) · Badge (2) · Tile head (3) · **Day ring** (6) · Food line · Detected item · Product row · Option row · Ingredient row · Meal row |
| 03.6 Cards & surfaces | **Budget card** (Empty/Before/After/Over) · Last meal tile · Zest tile · Dinners tile · Recipe card · Snackbar · **Bottom sheet** (+ 4 swappable contents) · Notice card |
| 03.7 Feedback & AI | **Zest orb** (Small/Nav/Medium/Large × Idle/Thinking) · Insight card · Chat bubble · Status pill · **Lens** (Framing/Reading/Unsure/Dim) · **What-if card** |

## State management

- **Component states:** interactive components carry their states as variants (Default, Pressed, Disabled, plus Selected / Loading / At minimum where they exist). They're wired as interactive components:
  - *While pressing → Pressed* on buttons, rows, chips, tabs and cards;
  - *On tap → Selected* on filter chips, radio, toggle and segments.
- **App state:** lives in variable modes. The prototype switches them with *Set variable mode*:
  - adding breakfast moves Today from *Before breakfast* to *Breakfast added*;
  - *Undo* switches it back;
  - *Plan for dinner* sets *Dinner planned*;
  - *Apply adjustment* sets *Adjusted*.

  Bound to those modes:
  - texts;
  - the Budget card's `State` variant, so the ring and macros move together;
  - the Zest tile's `Type`;
  - snackbar visibility;
  - progress-bar lengths (bound as right padding).
- **Progress bars:** a Macro bar's fill always fills the track. The empty part is the track's right padding. Figma won't resize a layer inside an instance through the API, but it will override and bind padding, so bars can be data-driven.
- **AI-only motion:**
  - the Zest orb's *Thinking* state breathes (keyframes live in the component, so every instance inherits them);
  - the Lens bead orbits while Zest reads;
  - the What-if ring pulses the segment of the meal in question.

  Nothing else in the app moves.

## Rules

1. No detached instances. Change an icon through the `Icon` property and text through the text properties.
2. Colour is never typed in. If a role is missing, add a semantic token aliased to a primitive.
3. One Primary button per screen. Sticky buttons sit on an opaque veil and never cover content.
4. Selection is always `accent/ember-strong` with white text (4.9:1). Commit actions are `action/primary`.
5. Facts, not verdicts: tags, the Over state and the What-if card state numbers and never use warning red for food.

## Verification

An independent audit (a separate Claude agent, read-only) checked every mockup for hand-typed values. Its findings and the fixes are in [`DS-AUDIT.md`](DS-AUDIT.md).
