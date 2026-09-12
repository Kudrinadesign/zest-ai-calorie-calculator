# Design-system audit — 12 September 2026

**What this is.** After the screens were rebuilt from components, a **separate Claude agent**
audited the file read-only, with no knowledge of how it was made, against one question: *does
every value on every mockup come from the design system, or is something typed in by hand?*

It checked, per node: fills, strokes, gradient stops, text styles, padding and gap, corner
radius, stroke weight, effects, layer opacity, hand-drawn copies of components, and detached or
missing instances — across the 10 main screens, the 11 edge-case frames and the 7 component
pages.

## Verdict

> "The screens are almost fully tokenised: every paint, gradient, text style, radius and stroke
> weight I checked is bound. No detached or remote components, no bindings that point straight
> at Primitives, and no broken variable references."

Clean with nothing to fix: Today, Add a product, Ask Zest, Recipes, E01, E02, E04, E05, E06,
E09 and the section header. Everything else had between one and three findings.

The auditor also cleared a false positive of its own: paint opacity on bound colours matches
the variable's own alpha on all 261 semi-transparent paints, so it is not an override.

## Fixed after the audit

| Finding | Fix |
|---|---|
| Four hand-typed text shadows over photos (Capture, E03, E03b, E05b) | Applied the **Shadow/Text on photo** effect style, which holds exactly those values |
| The orbiting bead's glow was typed in | Applied the **Glow/AI** style |
| "Zest" in the Welcome logo had a raw white override | Bound to `onbloom/primary` |
| The Analysing sheet used `ai/sphere-highlight` as its fill, `radius/tile-lg`, and `space/20` on top | Now `surface/raised`, `radius/sheet`, `space/12` — the same tokens the Bottom sheet component uses |
| Calendar day bars had a raw 8 px right padding | Bound to `space/8` |
| Status bar wifi and battery strokes were raw (1.5 / 1) | Bound to `stroke/control` and `stroke/hairline` |
| A hidden, hand-drawn "back" control left over on History | Removed |
| Primitives were not hidden from publishing | `hiddenFromPublishing = true` — raw values can't be picked by anyone consuming the library |
| Macro stat bars stopped short of the numbers (also reported by Sofia) | The bar now fills the row, and every bar's length is derived from its own value ("96 / 120 g" → 80 %) |

## Deliberately left, and why

- **Bar lengths as padding.** A Macro bar's fill length is the track's right padding. On Today
  and Recipe detail it is bound to prototype variables (`day/*-rest`, `recipe/*-rest`) so the
  bars move with the state. On screens where the number is fixed content (Result, History, E07,
  E08) the padding stays a plain override: it is data, not a spacing token, and inventing a
  token per bar would make the system worse.
- **The Analysing sheet stays hand-built.** It should be a Bottom sheet instance, but its
  contents animate (items appear one by one, the progress bar fills, the orb breathes) and
  Figma won't write keyframes onto layers inside an instance. It now uses the sheet's tokens.
  The same reason keeps its progress bar out of the Macro bar component.
- **iOS status bar geometry.** The signal and battery corner radii (1, 2, 3.5) are system-glyph
  drawing, not product radii.
- **Glows reuse `blur/*` tokens.** `blur/control` and `blur/deep` are named for glass, but the
  radii are right for the two layer-blur glows; a separate token would add a name without a
  reason.
- **Seven glass containers repeat by hand** (the Result items card, the recents card, "Why this
  fits you", ingredients, calendar, day summary, product card). They are fully tokenised; a
  generic "panel" component is worth adding if the file grows.

## Token hygiene

Duplicate values are mostly intentional aliases — `action/capture` = `action/primary` (the
camera commits), `line/focus` = `accent/ember-strong` (focus uses the selection colour),
`line/error` = `action/danger`. They exist so the role can change independently later.

Genuinely redundant and merged during the pass: 17 auto-generated `tint/*` tokens created while
binding leftover colours were folded into the existing `fade/*`, `scrim/*` and `glow/*` tokens,
and their primitives were deleted.

Still open, low priority: `opacity/40` next to `opacity/disabled` (same value, different
meaning), 16 value-named opacity tokens created by the binding pass, and Brand/Wordmark sitting
very close to Head/XL.
