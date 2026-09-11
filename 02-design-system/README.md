# Design system

`foundations.png` — colour, the bloom recipe, the type ramp, spacing and radius.
`components.png` — the component library.

Built as native Figma variables, styles and components, so the screens contain no
hardcoded values. Changing a token re-colours the whole product; the direction was
switched once mid-project and the screens followed automatically.

## Foundations

- ~53 variables across `ground/*`, `surface/*`, `bloom/*`, `glass/*`, `ink/*`,
  `onbloom/*`, `accent/*`, `action/*`, `macro/*`, `track/*`, `space/*`, `radius/*`
- 11 text styles, all Manrope: `Head/XL·L·M`, `Text/Title·Body·S·Label·Caption`,
  `Metric/XL·L·S`

| Role | Token | Value |
|---|---|---|
| Committing action, nav camera | `action/primary` | `#9E2044` |
| State — selected, progress, shutter | `accent/ember` | `#D7650E` |
| Protein · Carbs · Fat | `macro/*` | `#4550D7` `#FBC357` `#CE4A34` |
| Opaque surface — nav, input fields | `surface/raised` | `#FFFFFF` |
| Suggestion tiles — recipe teaser, Zest's reply | `glass/peach` | `#F4BFA5` at 66 % |

## Components

`Logo` (mark, horizontal, stacked) · `StatusBar` (dark, light) ·
`Nav` (Today, Recipes, Zest, History active) · `Button` (Primary, Secondary, Danger × L 46, M 38) ·
`Chip` · `Badge` · `RoundControl` (back, close, edit, flash)

## The rules worth knowing

**One burgundy button per screen.** Primary sits at the bottom, full width, and commits
something; pressing it returns to Today. Screens that have one hide the nav.

**Four places and one verb.** The nav holds Today · Recipes · Zest · History, each with a
label; the active one sits on a soft peach pill. The camera in the middle is the verb and
opens Capture from every place.

**`‹` and `×` mean different things.** `‹` goes one step back. `×` leaves a flow without
saving.

**Controls are never the colour of the atmosphere.** The bloom never borrows
`action/primary`; ember marks state and the shutter. Red appears only on destructive
actions.

**Every macro hue has a text-safe twin.** `macro/protein` is for bars and
`macro/protein-ink` is for the number beside it.
