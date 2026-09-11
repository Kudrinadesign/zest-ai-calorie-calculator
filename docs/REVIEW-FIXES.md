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
