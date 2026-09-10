# Design system

`foundations.png` — colour, the bloom recipe, the type ramp, spacing and radius.
`components.png` — the component library.

Built as native Figma variables, styles and components, so the screens contain no
hardcoded values. Changing a token re-colours the whole product; the direction was
switched once mid-project and the screens followed automatically.

## Foundations

- ~50 variables across `ground/*`, `bloom/*`, `glass/*`, `ink/*`, `onbloom/*`,
  `accent/*`, `action/*`, `macro/*`, `track/*`, `space/*`, `radius/*`
- 11 text styles, all Manrope: `Head/XL·L·M`, `Text/Title·Body·S·Label·Caption`,
  `Metric/XL·L·S`

## Components

`Logo` (mark, horizontal, stacked) · `StatusBar` (dark, light) ·
`Nav` (Today, Recipes, Zest, Profile active) · `Button` (Primary, Secondary, Danger × L, M) ·
`Chip` · `Badge` · `RoundControl`

## The two rules worth knowing

**Controls are never the colour of the atmosphere.** The committing action is burgundy
`#6B1B33` on every screen with no exceptions. Ember is reserved for state and for the
capture button. Red appears only on destructive actions.

**Every macro hue has a text-safe twin.** The graphic values are too light to carry type,
so `macro/protein` is for bars and `macro/protein-ink` is for the number beside it.
