# Progress

Snapshot of where the work stands, so it can be picked up without re-reading the whole
conversation.

## Figma file

`https://www.figma.com/design/mak5NZxh6OuT55iBLTpGD1/` — file key `mak5NZxh6OuT55iBLTpGD1`

| Page | State |
|---|---|
| `00 · Cover` | empty — still to do |
| `01 · Branding` | logo exploration (3 marks) + stylescape 4000 × 2000 |
| `02 · Foundations` | colour, bloom recipe, type ramp, spacing, radius |
| `03 · Components` | Logo, StatusBar, Nav, Button, Chip, Badge, RoundControl |
| `04 · Screens & Prototype` | 13 screens, wired, start point on Welcome |
| `05 · Flow map` | empty — still to do |

## Screens built

S01 Welcome · S02 Add · S03 Today · S04 Capture · S05 Analysing · S06 Result ·
S07 Ask Zest · S08 Add a product · S09 Recipes · S10 Recipe detail · S11 History ·
S12 Saved · S13 Profile

## Still to do

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
3. Export screens to `03-screens/` as PNGs
4. Push to a public GitHub repository, verify from incognito
5. Video walkthrough covering all three deliverables

## Decisions worth defending on video

- **The bloom is data.** On Today its hues are sampled from the day's meals.
- **Controls are never the colour of the atmosphere.** Burgundy action, no exceptions;
  ember reserved for state and the capture button.
- **No error red in nutrition data.** A copy rule expressed as a colour decision.
- **The logo shows state.** The arc in the mark is the remaining budget.
- **Every macro hue has a text-safe twin**, because the graphic values fail contrast.
- **Nothing duplicates the navigation.** Tiles that link to a destination carry content
  (a message, three recipes); bare duplicate controls were removed.

## Notes for whoever continues

- `node.screenshot()` inside `use_figma` can return a **stale render**. When something
  looks wrong, verify with the separate `get_screenshot` tool before chasing a bug that
  is not there.
- `resize()` resets auto-layout sizing to `FIXED`. Set `layoutSizingVertical = "HUG"`
  *after* resizing, or cards collapse to the resize height.
- Setting `vectorPaths` normalises the path bounding box to `0,0`; position the vector
  afterwards or it jumps.
- Figma's `query()` attribute matcher breaks on values containing spaces — use
  `[name*=Word]`.
- Prototype `NAVIGATE` destinations must be top-level frames **on the same page**, and a
  frame cannot navigate to itself.
- Arc commands (`A`) are not supported in `vectorPaths`; use cubic curves.
