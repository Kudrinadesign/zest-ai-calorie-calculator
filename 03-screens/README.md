# Key screens

Exported from Figma at 390 × 844 (iPhone 14/15). All ten are connected in the prototype;
the start point is Welcome.

| File | Screen | Kind | What it is for |
|---|---|---|---|
| `00-flow-map.png` | Flow map | — | Every screen, every link, the three kinds and their rules |
| `01-welcome.png` | Welcome | entry | The promise, in one sentence, plus the mark |
| `02-today.png` | Today | place | The day's budget, the week, the last meal, Zest's read |
| `03-capture.png` | Capture | flow | Viewfinder — the plate inside the ring; Photo · Barcode · Type it |
| `04-analysing.png` | Analysing | flow | Items surface one by one, so the AI's work is legible |
| `05-result.png` | Result | flow | Total, macros, Zest's observation, every portion editable |
| `06-add-a-product.png` | Add a product | flow | Search or barcode, with a portion stepper |
| `07-ask-zest.png` | Ask Zest | place | The assistant does the arithmetic, not the person |
| `08-recipes.png` | Recipes | place | Ranked by what is still left today |
| `09-recipe-detail.png` | Recipe detail | detail | Carries **Why this fits you** — the second user story |
| `10-history.png` | History | place | Month calendar and what was eaten on the chosen day |

## How the screens connect

Three kinds of screen, and each kind always behaves the same way.

| Kind | Screens | Top-left | Bottom | Arrives by |
|---|---|---|---|---|
| **Place** | Today, Recipes, Zest, History | — | the nav | dissolve, 300 ms |
| **Detail** | Recipe detail | `‹` one step back | one burgundy button | slides in from the right |
| **Flow** | Capture → Analysing → Result, Capture → Add a product | `×` leaves without saving | one burgundy button | rises from the bottom |

```
Welcome ──▶ Capture                     (Scan my first meal)
   └──────▶ Today                       (I already have an account)

Nav, on every place:  Today · Recipes · [ camera ] · Zest · History
                                         └──▶ Capture

Capture ──┬── shutter / library ──▶ Analysing ──(auto)──▶ Result ──▶ Today
          ├── Barcode ────────────▶ Add a product ───────────────────▶ Today
          └── Type it ────────────▶ Add a product

Today ──┬── week strip ───────▶ History
        ├── Zest tile ────────▶ Zest
        └── Dinners that fit ─▶ Recipes ──▶ Recipe detail ──▶ Today

Zest ──┬── Swap for something lighter ──▶ Recipes
       └── Add it to my day ────────────▶ Today
```

Three rules hold everywhere:

1. `‹` goes one step back. `×` closes a flow without saving.
2. The camera in the nav always opens Capture, from every place.
3. Every burgundy button commits something and returns to Today, where it lands.
