# Edge cases

A happy path shows what the product does when everything goes right. These nine screens
show what it does when it doesn't: the camera is pointed at the wrong thing, the model is
unsure, the network drops, the day goes over plan.

Every case keeps the product's rules:

- **Fact first, no verdicts.** Say what happened in numbers, never judge it.
- **One way forward.** One burgundy button that fixes the situation; a secondary for the
  alternative.
- **Nothing is lost.** No case throws away what the person already did.
- **The AI is honest about itself.** When it doesn't know, it says so, and says how sure it
  is.

| File | Case | What Zest does |
|---|---|---|
| `E01-no-plate-found.png` | The photo has no plate in it — too close, blurred, or not food | Says so plainly, dashes the ring, offers **Retake the photo** or **Type it instead**. Nothing was added. |
| `E02-two-dishes-look-alike.png` | The model can't tell two dishes apart | Shows both with its confidence (82 % / 18 %) and asks. The likelier one is pre-selected. |
| `E03-too-dark.png` | The kitchen is too dark to read the plate | The ring goes dashed, the pill names the problem, and the flash button lights up in the state colour — the fix is the thing that glows. |
| `E04-no-connection.png` | The network drops while the photo is being read | The orbit stops, the photo is queued on the phone, and Zest promises a notification when it's read. Back to Today, nothing lost. |
| `E05-barcode-not-in-the-list.png` | A barcode that isn't in the database | Explains, then turns it into a contribution: photograph the label once and the next scan works for everyone. |
| `E06-past-the-budget.png` | The day goes 120 kcal over plan | Stated as a fact in the clay tone — "120 kcal past 2,400 · 5%" — and Zest adds "Tomorrow starts fresh." No red, no "you failed". |
| `E07-first-day.png` | The first day, nothing logged yet | The bloom is sampled from what you ate, so with nothing eaten it is almost colourless. Every tile says where the first plate will land. |
| `E09-camera-access-off.png` | The camera permission is off | Says why the camera is needed and that photos stay on the phone; one button turns it on, a link lets you type instead. |
| `E08-correcting-an-estimate.png` | The estimate is wrong and the person fixes it | A stepper corrects the avocado from 80 g to 120 g, the meal total updates, and Zest learns: "I'll start from 120 g next time." |

In the prototype each case is its own flow (`Edge · …` in Present mode), and each one
returns to the happy path through its own button.

## Motion

Each case animates by the product's one motion rule — movement means the AI is working —
so the motion names the state: searching (E01, the dashed ring drifts by a whole number
of dashes so the loop is seamless), asking (E02), pointing at the fix (E03, the flash
pulses), waiting (E04, the orbit is still and the bead only breathes), answering (E05),
stating a fact (E06, the bars reach past the end), inviting (E07), learning (E08).
