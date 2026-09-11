# Progress

Snapshot of where the work stands, so it can be picked up without re-reading the whole
conversation.

## Figma file

`https://www.figma.com/design/mak5NZxh6OuT55iBLTpGD1/` — file key `mak5NZxh6OuT55iBLTpGD1`

| Page | State |
|---|---|
| `00 · Cover` | empty — still to do |
| `01 · Branding` | logo exploration (3 marks) + three stylescapes 4000 × 1000 (Natural light · The plate is data · No verdicts) |
| `02 · Foundations` | colour, bloom recipe, type ramp, spacing, radius |
| `03 · Components` | Logo, StatusBar, Nav, Button, Chip, Badge, RoundControl |
| `04 · Screens & Prototype` | 10 screens, wired, start point on Welcome |
| `05 · Flow map` | empty — still to do |

## Screens

Ten screens remain. **Add (sheet), Saved and Profile were deleted on purpose — do not
bring them back.**

S01 Welcome · S02 Today · S03 Capture · S04 Analysing · S05 Result · S06 Add a product ·
S07 Ask Zest · S08 Recipes · S09 Recipe detail · S10 History

## Round 2 — softer colour, button logic, screen logic (11 Sept)

### Done

- **Palette softened** through the variables (bloom, ink, macro, accent, action), then the
  hardcoded gradient stops of the old palette were remapped on the screens and components.
- **Nav rebuilt**: four places with labels + one verb in the middle.
  `Today · Recipes · [camera] · Zest · History`. The active place sits on a soft peach
  pill. The Profile variant became `Active=History` (Profile screen no longer exists).
- **Capture (S04) redesigned**: title "Log a meal", thin white ring instead of the orange
  beam, "Plate in view · hold still" detection pill, white-ring shutter (no longer looks
  like the Zest orb), modes `Photo · Barcode · Type it`, duplicate search button removed,
  dark scrim behind the dock, close/flash are now `RoundControl` instances.
- **Zest insight tiles** (Today, Result, Recipe detail) moved off the loud orange gradient
  to a peach wash with ink text.

### Sofia's manual edits in Figma — these are the intended values

- `#9E2044` — every primary CTA, the Ask Zest send button, the camera button in the nav
- `#D7650E` — state: selected day, shutter disc, analysing progress and checks
- `#4550D7` / `#FBC357` / `#CE4A34` — protein / carbs / fat bars
- `#FFCB2F` — butter/leaf bloom ellipses (also at 60 %)
- `#F4BFA5` at 66 % — Recipes tile on Today, Zest's reply bubble
- Today's Zest tile: gradient `#8E4157 → #FCEDDE`
- Nav Zest orb gradient `#E9A452 → #FF4901`; Welcome logo recoloured (olive leaf `#A2AA0C`)
- **Primary button height 46** (was 60), label Manrope Medium 13
- White search field on Add a product; name on Today is "Dmytro"

### Folded into the design system (done)

1. Variables take Sofia's values; new tokens `surface/raised` (nav, inputs) and
   `glass/peach` (suggestion tiles). Every hardcoded colour on the screens is bound again.
2. `Button` L = 46, M = 38. `Nav` is opaque white with 8 px side padding, the camera
   uses `action/capture` (= `#9E2044`), the new orb gradient. `Logo` has the olive leaf
   and the cream → rust fruit. Selected `Chip` is solid ember.
3. The hand-made CTAs are `Button` instances again, each with its own label (Welcome
   "Scan my first meal", Add a product "Add 180 g · 175 kcal", Recipe detail
   "Cook this · logs 480 kcal", Result "Add to my day").
4. Screen logic: Ask Zest and History are places (nav, no back); Result and Analysing use
   `×` (`RoundControl` instances); the duplicate camera on Add a product is gone; the
   bookmark on Recipe detail no longer navigates; Last meal and the avatar on Today no
   longer lead to deleted or wrong screens.
5. Every prototype link rewired with the transition system below (~40 links).
6. Polish: Welcome bloom no longer borrows the action colour (→ mulberry), Welcome
   wordmark white again, the Zest orb is visible on light tiles, all recipe cards share
   one title style, Ask Zest spacing balanced.
7. Frames renumbered S01–S10 in flow order; PNGs re-exported; Foundations labels synced
   with the live variables (they still showed the Sunlit Glass values).

### Next

- Play the prototype once in Present mode to confirm the direction of the
  Move-in / Slide-in transitions (the API names the direction of travel).

### Navigation model

| Kind | Screens | Top-left | Bottom | Transition in |
|---|---|---|---|---|
| Place (tab) | Today, Recipes, Zest, History | — | Nav | Dissolve 300 ms, ease-out |
| Detail | Recipe detail | ‹ back | one CTA | Slide in from right, gentle spring |
| Capture flow | Capture → Analysing → Result, Capture → Add a product | × leaves the flow | one CTA | Move in from bottom |

- `×` closes a flow without saving (on Capture it returns to where you were; later in the
  flow it returns to Today). `‹` always goes one step back.
- The camera in the nav always opens Capture, from every tab.
- Every committing button returns to Today, where the meal lands.

## Still to do (from round 1)

1. **Edge cases** — explicitly requested, deliberately left until the happy path was
   complete. Candidates worth designing rather than listing:
   - the photo contains no food, or the model is unsure which of two dishes it is
   - a plate is photographed in the dark, or half out of frame
   - the estimate is wrong and the person corrects it — what the correction teaches
   - going over the day's budget, said without a verdict (rule 03)
   - no connection while the photo is being analysed
   - a barcode that is not in the database
   - the first day, with nothing logged yet (empty state)
   - a day skipped entirely, then reopened a week later
2. **Cover page** and **flow map** page
3. Push to a public GitHub repository, verify from incognito
4. Video walkthrough covering all three deliverables

## Decisions worth defending on video

- **The bloom is data.** On Today its hues are sampled from the day's meals.
- **Controls are never the colour of the atmosphere.** Burgundy action, no exceptions.
- **No error red in nutrition data.** A copy rule expressed as a colour decision.
- **The logo shows state.** The arc in the mark is the remaining budget.
- **Every macro hue has a text-safe twin**, because the graphic values fail contrast.
- **Nothing duplicates the navigation.** Tiles that link to a destination carry content
  (a message, three recipes); bare duplicate controls were removed.

## Notes for whoever continues

- `node.screenshot()` inside `use_figma` can return a **stale render**. When something
  looks wrong, verify with the separate `get_screenshot` tool before chasing a bug that
  is not there.
- A paint bound to a variable must also carry the variable's resolved colour as its
  literal `color`, or it renders as the literal (black) until the file refreshes.
- `resize()` resets auto-layout sizing to `FIXED`. Set `layoutSizingVertical = "HUG"`
  *after* resizing, or cards collapse to the resize height.
- Setting `vectorPaths` normalises the path bounding box to `0,0`; position the vector
  afterwards or it jumps.
- Figma's `query()` attribute matcher breaks on values containing spaces — use
  `[name*=Word]`.
- Prototype `NAVIGATE` destinations must be top-level frames **on the same page**, and a
  frame cannot navigate to itself.
- Overlay settings (`overlayPositionType`, background) are read-only in the Plugin API.
- Arc commands (`A`) are not supported in `vectorPaths`; use cubic curves.
