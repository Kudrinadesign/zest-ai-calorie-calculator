# Edge cases

> When the app is used in unexpected conditions, Zest keeps the rules: fact first, no
> verdicts, one clear way forward.

A happy path shows what the product does when everything goes right. These screens show what
it does when it doesn't:
- the camera is pointed at the wrong thing;
- the model is unsure;
- the network drops;
- the day goes over plan.

They sit in the **Edge cases** section below the main flow on the `04 · Screens & Prototype` page.
- **Format:** 390 × 844 frames, evenly spaced, content in Auto Layout.
- **Built from:** design-system instances only (Nav bar, Bottom sheet with swappable content, Lens, Status pill, Search field, Notice card, Budget card, Macro stat, Zest tile…). Every value comes from the variables.
- **Why a Section and not an Auto Layout frame:** screens nested inside a frame stop being prototype frames, and Retake, "Type it" and "Back to Today" would stop working. So the screens sit in a Figma Section on an exact grid.

Every case keeps the product's rules:
- **Fact first, no verdicts.** Say what happened in numbers, never judge it.
- **One way forward.** One primary button that fixes the situation, plus a secondary for the alternative.
- **Nothing is lost.** No case throws away what the person already did.
- **The AI is honest about itself.** When it doesn't know, it says so, and says how sure it is.

| Frame | Case | What Zest does | Links |
|---|---|---|---|
| E01 · No food detected | Too close, blurred, or not food | Blurred photo, dashed lens, "Nothing to read". Sheet: *I can't find a plate here*. Footnote: nothing was added. | Retake → Capture · Type it → Add a product |
| E02 · Ambiguous recognition | Two dishes look alike from above (top-down pasta) | Sheet with the orb: two Option rows, *Pesto pasta ≈ 560 kcal · 82 % sure* (selected) and *Pasta with courgette ≈ 480 kcal · 58 % sure*. | Either option / It's pesto pasta → Result · Neither → Add a product |
| E03 · Image too dark | Low light | Darkened bowl, dim lens, status *Too dark to read the plate*, instruction *Turn on the flash, or move towards the light.*, flash highlighted. | Flash → **E03b · Flash on** (correctly exposed), and back |
| E04 · No internet connection | The network drops while reading | Lens stops, status *Offline · photo saved*. Sheet: *No connection* with the queued meal card (Breakfast · 09:12 · Saved on this phone · QUEUED). | Back to Today · Type it → Add a product |
| E05 · Barcode not found | Barcode `5 900532 300047` isn't in the list | Search field in the Error state, Notice card *Not in our list yet*, *Or pick something close* with three Product rows. | Photograph the label → **E05b · Nutrition label camera** |
| E06 · Daily target exceeded | The day went 120 kcal past 2,400 | Budget card *Over*: ring 120 past 2,400, *5% over plan*, macros 124/120 · 262/260 · 86/80. Protein card *4 g past goal*. Zest: *Dinner went 120 kcal past plan, 5%. Tomorrow starts fresh at 2,400.* *Breakfast ideas · Your 3 favourites*, ordinary breakfasts, no "make up for it". | Breakfast ideas → Recipes |
| E07 · First day, empty state | Nothing logged yet | Budget card *Empty* (2,400 kcal to spend, 0/120 · 0/260 · 0/80), Last meal *Nothing yet · It will land here*, *Protein to go 120 g*, Zest invites the first photo. | Take a photo → Capture |
| E08 · Correcting an estimate | An estimate looks wrong | Tapping a line on Result opens a sheet with a Stepper (≈ 60 g · 160 kcal). | Save / Remove this line → Result |
| E09 · Camera access is off | Camera permission denied | Dim lens with a crossed-out camera. Sheet: why the camera is needed, photos stay on the phone. | Turn on the camera → Capture · Type it → Add a product |

About the brief: it arrived cut off after item 7. E08 and E09 continue the earlier set of
edge cases in this project, rebuilt the same way.

## Motion

Motion means the AI is working, and nothing else moves:
- E01, E03, E04 and E09: the lens is dim and still, because Zest isn't reading.
- E02: the Zest orb in the sheet breathes, because Zest is asking.
- E03b: the reading animation stays on the exposed frame.
