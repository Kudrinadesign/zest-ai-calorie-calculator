# Review — what was fixed

A reviewer scored the nine static screens **7.8 / 10** ("strong Trainee — would invite to
interview") and listed what must change before a client sees it. Everything on the
"fix first" list and every high-severity point is addressed below.

## Critical

| Issue | Fix |
|---|---|
| Capture showed a salad, Analysing and Result an avocado toast | Capture now shows the same toast, framed so the whole dish sits inside the ring; the hint says "Fit the whole dish inside the ring". |
| Result percentages disagreed with Today's targets (42 % and 36 %) | Recomputed from the same targets as Today — protein 21 / 120 g = **18 %**, carbs 38 / 260 g = **15 %**, fat 33 / 80 g = 41 % — and the bars redrawn to match, on the screen and in every copy of it (stylescapes, cover, flow map). |

## High

| Issue | Fix |
|---|---|
| Miso salmon hid that it takes fat past the target (71 + 14 = 85 g > 80 g) | *Why this fits you* now states the trade-off and a way out: "Trade-off: 14 g fat takes today 5 g past 80 g. Halve the sesame oil to stay inside." |
| Recognised weights looked exact | Every detected weight is "≈"; the list is titled "What Zest found · estimated"; the total reads "≈ 264 g on the plate"; Analysing says "estimating each portion · about 2 s". |
| Found list had no units for calories | "≈ 60 g · 160 kcal" on every line. |
| Editing a found item wasn't shown; pencil and "tap to adjust" overlapped | The pencil is gone — the lines are the one way to edit. Tapping a line opens the correction sheet (E08), where the portion is changed and Zest learns from it. |
| Sticky buttons covered content | The veils under the bottom buttons and the nav are opaque where the bar sits. |
| Planning a meal and logging it were one action ("Cook this · logs 480 kcal") | Two actions: **Start cooking** and **Plan for dinner · 1 serving**. Ask Zest's chip is "Plan it for dinner". |
| Nothing happened after *Add to my day* | New screen **S11 · Today — meal added**: "Added to breakfast · 516 kcal · 540 kcal left of 2,400 · Undo". |

## Medium and low

| Issue | Fix |
|---|---|
| Judgemental wording — *took*, *used … budget*, *owe* | "Breakfast was / is 41 % of today's fat", "38 g protein covers the 24 g still to go". |
| Zest ignored the protein still to go | "That leaves 120 kcal and 10 g protein to go — a Greek yoghurt covers both." |
| Welcome chips looked like buttons; "No verdicts" too abstract; login looked like a caption | A plain list with dots; "Every estimate is editable", "No food shaming"; "I already have an account · **Log in**" as a real link. |
| Low-contrast text on light areas | Welcome's lower half, the Capture modes and the pending Analysing row moved to readable ink / 90 % white. |
| Number formatting | "2,400", "1,860" everywhere. |
| Calendar bars had no scale; two different "Today"s on History | "Bar length = share of the day's 2,400 kcal. A clay bar means the day went over."; the button is "Back to today", the badge stays a status. |
| Recipes copy | "Every recipe fits both targets." |
| Why single out protein on Today | The card is "Protein to go" — protein is the person's goal (120 g a day), which is also what Recipes ranks by. |
| No permission / failure states | New edge case **E09 · Camera access is off**, alongside the eight others (no plate, two dishes, too dark, offline, unknown barcode, over budget, first day, correction). |

## Not changed, on purpose

- **The orange shutter vs the burgundy button.** Burgundy commits; ember is state and the
  shutter — the capture button is where logging *starts*, not where it is committed. The
  rule is written in the design system.
- **Onboarding goals, allergies, recipe search, sorting, saved state on cards, cooking
  mode, chat history** — real, but outside the two user stories in the brief.

---

# Second review — 8.7 / 10

The reviewer confirmed the fixes above and listed what was still open. All of it is done.

| Issue | Fix |
|---|---|
| E06 showed "Protein to go — 124 g" while the day was already 4 g past the goal | The card reads **Protein · 4 g past goal**, 124 g. |
| Today did not change after *Add to my day* — the meal was already counted | The story is now one afternoon: **Today (before)** shows 1,344 kcal eaten and **1,056 left** (protein 75 / 120, carbs 172 / 260, fat 38 / 80) with Zest's nudge *"Breakfast isn't logged yet — add it from your photos"*. The breakfast photo is picked from the library on Capture → Analysing → Result (**Breakfast · 09:12**, 516 kcal) → **Today (after)**: 1,860 eaten, **540 left** (96 / 120, 210 / 260, 71 / 80) with *"Added to breakfast · 516 kcal · Undo"*. The after-state is exactly what Recipes, Ask Zest and History already show. |
| The Miso salmon advice could not be applied — and its maths did not hold (1 tsp of sesame oil is ~2 g fat a serving) | The trade-off now names a change that actually closes the gap: *"100 g of salmon instead of 140 g keeps it inside"* — 40 g less salmon is −83 kcal, −8 g protein, −5 g fat, so the day lands at 80 / 80 g. *Plan for dinner* stays available: the choice is the person's. |
| *Start cooking* looked disabled | Secondary buttons are white with a 22 % ink edge and a semibold label (new token `action/secondary-edge`). |
| "Light mornings" after a day over budget read as compensation | The tile is **Breakfast ideas · Your 3 favourites** — nothing to make up. |
| History relied on colour for over-budget days | Over-budget dates carry a **+**; the legend says "A + marks a day that went over". |
| Planning vs logging after the button | *Plan for dinner* (Recipe detail, Ask Zest) lands on **Today — dinner planned**: *"It logs when you mark it eaten"*. |

---

# Third round — making it work, not just look right

| Asked for | Done |
|---|---|
| *Apply adjustment* with automatic recalculation | Recipe detail is bound to a `Prototype · Recipe` variable collection. *Apply adjustment · −5 g fat* switches it to *Adjusted*: kcal, the three reasons, protein, fat, both bars and the salmon amount change in place; *Back to 140 g* switches back. |
| Updated Today after *Add to my day*, with Undo | Today is bound to `Prototype · Day` (before / breakfast added / after / dinner planned). *Add to my day* switches the mode and navigates; the budget, macros, bars, protein-to-go and Zest's line recalculate and the snackbar appears. *Undo* restores the before state. |
| A clickable main scenario | New flow **Main · log breakfast → plan dinner**. Every link was checked two ways: a graph walk over all prototype reactions (no broken links; all ten screens reachable from Welcome) and a real click-through of the published prototype in a logged-out browser. |
| Sticky buttons and contrast | See [`ACCESSIBILITY.md`](ACCESSIBILITY.md): three token fixes, three text-on-bloom fixes measured on real pixels, 44 px round controls. |
| Problem, hypothesis, role of AI, success metric | README *The case* and a **The case** frame on the Cover page. |
| 3–5 real usability tests | Not possible from here — I can't recruit or observe people, and I won't invent results. [`USABILITY-TEST-PLAN.md`](USABILITY-TEST-PLAN.md) has the script, seven tasks with success criteria, what to note and an empty results table. |
