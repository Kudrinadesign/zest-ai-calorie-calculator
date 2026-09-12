# Progress

Snapshot of where the work stands, so it can be picked up without re-reading the whole
conversation.

## Figma file

`https://www.figma.com/design/mak5NZxh6OuT55iBLTpGD1/` — file key `mak5NZxh6OuT55iBLTpGD1`

| Page | State |
|---|---|
| `00 · Cover` | cover 1920 × 1080 (exported as `cover.png`) — **thumbnails are pre-rebuild, refresh before submitting** |
| `01 · Branding` | logo exploration (3 marks) + main collage **Stylescape · Zest** + four supporting stylescapes 4000 × 1000 (Where it comes from · Natural light · The plate is data · No verdicts) |
| `02 · Foundations` | colour, bloom, type, spacing, radius + token architecture, sizes & strokes, effects, extra text styles |
| `03 · Components` | overview: token layers, state management, index of the family pages, Logo |
| `03.1 – 03.7` | 64 components with all states — Icons · Actions · Inputs & selection · Navigation · Data display · Cards & surfaces · Feedback & AI |
| `04 · Screens & Prototype` | 10 screens (built from instances) + **Edge cases** section (9 cases + E03b, E05b); 13 prototype flows named after the brief's user stories |
| `05 · Flow map` | rebuilt around the two user stories — Story 1 (dish / product), Story 2 (recipe), supporting |

## Round 7 — design system, rebuild, audit (11–12 Sept)

- **Design system built properly:** 354 variables in 5 collections (Primitives → semantic,
  Typography, two Prototype collections), 16 text styles and 8 effect styles bound to
  variables, 64 components with Default / Pressed / Disabled / Selected / Loading states wired
  as interactive components.
- **All screens rebuilt from instances**; the old Button / Chip / RoundControl / Badge / Nav
  sets were migrated and deleted.
- **Today's budget** is now a ring with kcal left plus macros against their targets; the state
  switches with the day's mode (two ring instances toggled by `day/breakfast-in`, because a
  variant bound to a variable does **not** resolve inside a nested instance).
- **Ask Zest** answers with a What-if card: the ring shows where the day lands with the meal,
  the pale segment (the meal in question) breathes.
- **Photography:** the capture flow is top-down with the whole dish centred in the lens.
- **Edge cases** rebuilt to the spec as a section below the main flow.
- **Independent audit** by a separate Claude agent — see [`DS-AUDIT.md`](DS-AUDIT.md).
- **Exports re-done at 3x** (1170 × 2532) after feedback that the screens looked small.

### Still to do

1. **Video walkthrough** (English, showing branding, design system and final designs) — the
   brief requires it; not recorded.
2. **Publish the GitHub repo** and check every link in incognito — not published yet, on Sofia's
   instruction.
3. Refresh the Cover and "The case" thumbnails, which still show pre-rebuild screens.
4. Real usability sessions (the plan and the session page are ready; no results invented).

## Screens

Eleven screens now (S11 · Today — meal added was added in round 4). **Add (sheet), Saved and Profile were deleted on purpose — do not
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

## Round 3 — stylescapes, AI motion, edge cases (11 Sept)

- **Three stylescapes** 4000 × 1000 in the reference format, built from live screens,
  components and tokens: Natural light · The plate is data · No verdicts. The outdated v1
  stylescape was removed from Figma.
- **AI motion** (Figma Motion keyframes) on Capture, Analysing, Ask Zest and the Zest orb
  on insight tiles — verified from rendered video frames.
- **Eight edge cases** (E01–E08) on the Screens page, row at y = 1100, each its own
  prototype flow. Exports in `04-edge-cases/`.
- **Stylescape 00 · Where it comes from** — the moodboard: the peel → the mark and a drawn citrus cross-section, light not
  colour, the palette sampled with eyedroppers from a real plate, daylight photography.
- **Cover** and **Flow map** pages built.
- **Stylescape · Zest** — the main stylescape rebuilt as a reference-style mosaic: hard-edged
  tiles (idea, lens + 516, live Today, icons + voice, sampled plate + palette, type + 2.2 s)
  with stickers across the seams and text on a circle.
- **Edge-case motion** — every edge case animates by the same AI-only rule.
- **Yellows muted** at Sofia's request: `bloom/butter` `#EDD28E`, `macro/carbs` `#E6BC6A`.
- **Secondary button fixed**: new token `action/secondary` (ink at 7 %) — binding a paint to
  a variable drops the paint's own opacity, so the alpha has to live in the variable.

## Round 4 — review fixes (11 Sept)

A reviewer scored the static screens 7.8 / 10. Every critical and high-severity point is
fixed — see `docs/REVIEW-FIXES.md`. New: S11 · Today — meal added, E09 · Camera access is
off, a main collage stylescape, motion on every edge case.

## Round 5 — second review (8.7 / 10) fixed (11 Sept)

Today before/after made one coherent afternoon (1,056 → 540), E06 protein wording, honest
salmon adjustment, enabled-looking Secondary, no compensating breakfasts, a + on over-budget
days, Today — dinner planned. S09b (adjusted recipe) was removed by Sofia on purpose.

## Round 6 — prototype state, contrast, case (11 Sept)

Today and Recipe detail recalculate through variable modes (no extra frames — S11/S12 kept
disappearing, most likely through Figma undo). Main flow clicked through in the published
prototype. Contrast fixed and measured on real pixels. The case on the Cover page. Usability
test plan written; tests not run.

## Still to do

Figma file shared as "Anyone with the link · can view" and renamed to `project`; file and
prototype links in `links.md`, both checked from a browser with no Figma login.


1. Push to a public GitHub repository, verify from incognito
2. Run 3–5 usability sessions with `docs/USABILITY-TEST-PLAN.md` and fill in the results
3. Video walkthrough covering all three deliverables (script in `docs/VIDEO-SCRIPT.md`)

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
- Binding a paint to a variable resets the paint's `opacity` to 1 — put the alpha in the
  variable's value instead.
- Motion: `get_screenshot` shows only the resting state; verify with `export_video` and
  `ffmpeg` frame extraction.
- Arc commands (`A`) are not supported in `vectorPaths`; use cubic curves.
