# Cognitive walkthrough — 11 September 2026

**What this is:** an expert walkthrough of the seven tasks in
[`USABILITY-TEST-PLAN.md`](USABILITY-TEST-PLAN.md), done by Claude in the published
prototype, in a browser with no Figma login, clicking every step.

**What this is not:** a usability test. No participants took part; there are no success
rates, times or quotes. It predicts where a first-time user *could* struggle, so the real
sessions can check those points. The results table in the test plan stays empty until
real people have used the prototype.

For each step the method asks four questions: *Will they try to do the right thing? Will
they notice the control? Will they connect it with their goal? Will they see that it
worked?*

## Tasks

| # | Task | Prototype works? | Where a first-time user could stumble |
|---|---|---|---|
| 1 | Log this morning's breakfast from a photo | ✅ Today → Capture → library → Analysing → Result | The Zest tile ("Add it from your photos") has **no tap affordance** — "Dinners that fit" next to it has a chevron, this doesn't. On Capture the **library thumbnail is unlabeled** (46 px, bottom-left); someone looking for "this morning's photo" may press the shutter instead. |
| 2 | Is Zest sure? What if a line is wrong? | ✅ Any found line → correction sheet (E08), incl. the half-veiled one | "estimated" and "≈" are visible. "Tap a line to adjust" is an 11 px caption and the rows have **no edit affordance** (no chevron or pencil), so the fix depends on reading the caption. |
| 3 | Add it — what changed? | ✅ Today recalculates 1,056 → 540, macros, bars, Zest's line; snackbar | Clear. The changed numbers are not highlighted; the snackbar's second line ("540 kcal left of 2,400") carries the change. The snackbar covers the bottom of the "Dinners that fit" tile until dismissed. |
| 4 | Take it back | ✅ Undo → 1,056 | Clear — Undo is the only amber text on a dark bar. |
| 5 | Find a dinner that fits | ✅ Dinners that fit / nav → Recipes → Recipe detail | Clear. |
| 6 | Anything to know? Can you act on it? | ✅ Apply adjustment recalculates in place; Back to 140 g | The trade-off is a two-line 13 px sentence; the button label ("−5 g fat") carries the point if the sentence is skimmed. |
| 7 | Plan it — is it counted yet? | ✅ Plan for dinner → "Dinner planned · It logs when you mark it eaten" | Once the snackbar is gone, **Today shows no trace of the plan** — nothing to check when someone asks "is it counted?" later. After *Apply adjustment*, nothing says which version (480 or ≈ 400 kcal) was planned. |

## Predicted issues, by severity

| # | Issue | Severity | Suggested fix | Check in real sessions |
|---|---|---|---|---|
| W1 | Zest's nudge tile doesn't look tappable | Medium | Add "Add from photos ›" as a text button inside the tile | Task 1: do people tap the tile or go to the camera? |
| W2 | Library thumbnail on Capture is unlabeled | Medium | A "Library" caption under the thumbnail | Task 1: how many press the shutter instead? |
| W3 | Found lines have no edit affordance | Medium | A chevron on each line; keep the caption | Task 2: do people find the correction without prompting? |
| W4 | A planned dinner leaves no trace on Today | Medium | The Dinners tile becomes "Tonight · Miso salmon · planned · ≈ 400 kcal" | Task 7: can people answer "is it counted?" a minute later? |
| W5 | Snackbars cover content and don't auto-dismiss (prototype) | Low | Auto-dismiss after ~6 s in the build; in the prototype, a tap anywhere closes it | Task 3 |
| W6 | Undo, then Plan, shows after-breakfast totals | Low | Prototype limitation — a real build computes the day | Tell participants if they hit it |

## Verified along the way

- No link is broken; all ten happy-path screens are reachable from Welcome.
- The opaque veils under sticky buttons don't block taps on the list behind them.
- State changes survive navigation: Today keeps its mode when you leave and come back.
