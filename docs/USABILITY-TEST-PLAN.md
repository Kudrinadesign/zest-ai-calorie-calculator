# Usability test plan — 3 to 5 sessions

**Status: not run yet.** Nothing below is a result. An expert walkthrough of the same tasks
(no participants) is in [`COGNITIVE-WALKTHROUGH.md`](COGNITIVE-WALKTHROUGH.md) — its predicted issues W1–W6
are the things to watch for. The results section is an empty
template to fill in after real sessions — do not fill it with guesses.

## What we want to learn

1. Can someone log a meal from a photo **without help**, and do they notice that the
   numbers are estimates they can change?
2. After *Add to my day*, do they understand what changed on Today — and that **Undo**
   exists?
3. Can they find a dinner that fits, understand *why it fits*, and use **Apply
   adjustment**?
4. Do they understand the difference between **planning** a dinner and **logging** it?
5. How does the tone land — does anything feel like a verdict?

## Participants

3–5 people who have tried to count calories or macros in the last year (any app, or a
notebook). Avoid designers and people who have seen the file. 20–25 minutes each,
remote or in person, on a phone if possible.

## Setup

- Prototype: the **Main · log breakfast → plan dinner** flow — [link in `links.md`](../links.md)
  (starting point `S02 · Today`). On a phone, open it in the Figma app or the browser and
  add it to the home screen for full screen.
- Record the screen and voice with consent. Ask them to think aloud.
- One facilitator reads the tasks; don't explain the interface, don't help unless stuck
  for 60 seconds (then note it as an assist).

## Script

> Thanks for helping. We're testing the app, not you — there are no wrong answers. Please
> say what you're thinking as you go. It's an early prototype, so some things won't work;
> that's fine, just tell me what you expected.

### Tasks

| # | Task (read aloud) | Success looks like |
|---|---|---|
| 1 | "It's the afternoon. You had breakfast this morning and took a photo of it, but you haven't logged it. Add it." | Opens the camera (Zest tile or nav), picks the photo from the library, reaches Result. |
| 2 | "Is Zest sure about these numbers? If one looked wrong, what would you do?" | Mentions "≈ / estimated" and taps a line (or says they would). |
| 3 | "Add it to your day. What changed?" | Taps *Add to my day*; names at least one change on Today (540 left / the snackbar). |
| 4 | "Actually, you logged the wrong thing. Take it back." | Uses *Undo*. |
| 5 | "Find something for dinner that fits what's left today." | Reaches Recipes via *Dinners that fit* or the nav, opens a recipe. |
| 6 | "Is there anything about this recipe you should know before choosing it? Can you do something about it?" | Reads the trade-off; uses *Apply adjustment*. |
| 7 | "Decide to have it tonight. Has it been counted in your day yet?" | Taps *Plan for dinner*; answers "no, it logs when I eat it". |

### After each task

- Single Ease Question: *"How easy or difficult was that?"* 1 (very difficult) – 7 (very easy).
- "What did you expect to happen?" if they hesitated.

### At the end

- "Was there any moment the app felt like it was judging you?"
- "What would make you trust the numbers more?"
- "Would you use this instead of what you use now? Why / why not?"

## What to note

For each task: completed / completed with assist / failed · time on task · wrong taps ·
SEQ score · quotes. Also note any moment someone reads "≈" or the trade-off aloud.

## Known prototype limits (tell participants if they hit them)

- The day's numbers are scripted: after *Undo*, planning a dinner still shows the
  after-breakfast totals.
- *Start cooking*, the bookmark, recipe filters and the chat input are not wired.
- Barcode and *Type it* on the camera lead to one example product (Greek yoghurt).

## Results — to fill in after real sessions

| Participant | Profile | T1 | T2 | T3 | T4 | T5 | T6 | T7 | Notes |
|---|---|---|---|---|---|---|---|---|---|
| P1 | | | | | | | | | |
| P2 | | | | | | | | | |
| P3 | | | | | | | | | |
| P4 | | | | | | | | | |
| P5 | | | | | | | | | |

**Findings** (problem · how many participants · severity · proposed fix):

1.
2.
3.
