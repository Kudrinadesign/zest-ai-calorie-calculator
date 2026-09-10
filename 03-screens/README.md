# Key screens

Exported from Figma at 390 × 844 (iPhone 14/15). All thirteen are connected in the
prototype; the start point is Welcome.

| File | Screen | What it is for |
|---|---|---|
| `01-welcome.png` | Welcome | The promise, in one sentence, plus the mark |
| `02-add.png` | Add | The fork: photo, barcode, manual search, or ask Zest |
| `03-today.png` | Today | The day's budget, the week strip, the last meal, Zest's read |
| `04-capture.png` | Capture | Viewfinder — the plate held inside the light |
| `05-analysing.png` | Analysing | Items surface one by one, so the AI's work is legible |
| `06-result.png` | Result | Total, macros, Zest's observation, every portion editable |
| `07-ask-zest.png` | Ask Zest | The assistant does the arithmetic, not the person |
| `08-add-a-product.png` | Add a product | Search or barcode, with a portion stepper |
| `09-recipes.png` | Recipes | Ranked by what is still left today |
| `10-recipe-detail.png` | Recipe detail | Carries **Why this fits you** — the second user story |
| `11-saved.png` | Saved | Kept recipes, honest about the ones that no longer fit |
| `12-history.png` | History | Month calendar and what was eaten on the chosen day |
| `13-profile.png` | Profile | Goals, saved, history, settings |

## Flow

```
Welcome ──▶ Capture
   └──────▶ Today

Today ──┬── capture ──▶ Add ──┬── Photograph ──▶ Capture ──▶ Analysing ──▶ Result ──▶ Today
        │                     ├── Barcode ─────▶ Capture
        │                     ├── Search ──────▶ Add a product ──▶ Today
        │                     └── Ask Zest ────▶ Ask Zest
        ├── week strip ──────▶ History
        ├── Last meal ───────▶ Result
        ├── Zest tile ───────▶ Ask Zest
        └── Dinners that fit ▶ Recipes ──▶ Recipe detail ──▶ Today

Profile ──┬── Saved ──▶ Recipe detail
          ├── History
          └── Settings
```

Bottom navigation, identical everywhere: **Today · Recipes · Capture · Zest · Profile**.
