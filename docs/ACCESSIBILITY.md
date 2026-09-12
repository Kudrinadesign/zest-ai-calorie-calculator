# Accessibility check

WCAG 2.2 contrast targets: 4.5 : 1 for body text, 3 : 1 for large text (≥ 24 px, or
≥ 18.66 px bold) and for non-text UI. Ratios below were computed from the token values,
and (where text sits on the bloom or a photo), from the **real pixels** of the exported
screens (the background sampled under each text block).

## Token pairs

| Pair | Before | After |
|---|---|---|
| `ink/tertiary` on paper / porcelain (captions, meta) | 3.40 / 3.08 ✗ | **#6B635C** → 5.38 / 4.89 ✓ |
| White on `accent/ember` (selected date, selected chip) | 3.65 ✗ | **`accent/ember-strong` #BF540A** → 4.68 ✓: ember stays for bars, checks, the shutter |
| `onbloom/secondary` on mulberry | 62 % white → 3.87 (large only) | **82 %** → 5.54 ✓ |
| White on `action/primary` (buttons) | 7.65 ✓ |  |
| `accent/ember-deep` on `accent/ember-soft` (badges) | 5.01 ✓ |  |
| Macro inks on paper (protein / carbs / fat) | 7.65 / 6.11 / 6.01 ✓ |  |
| Amber *Undo* on the ink snackbar | 8.51 ✓ |  |

## Text on the bloom and photos (sampled from the exports)

| Where | Before | Fix | After |
|---|---|---|---|
| Welcome: body copy, 15 px | 3.48 ✗ | the bloom deepens under the copy (a soft plum "text shade"), text 100 % white | **8.48 ✓** |
| Recipes: subtitle, 15 px | 2.31 ✗ | same text shade, 92 % white | **6.35 ✓** |
| Ask Zest: headline, 24 px | 2.81 ✗ | it sits on the light part of the orb's halo, so it is set in ink | **5.90 ✓** |
| Today: subtitle, 30 px Light | 3.40 (large ✓) | `onbloom/secondary` 82 % | **4.68 ✓** |
| Result: top label on the photo scrim | 5.58 ✓ |  |: |

## Touch targets and sticky bars

- `RoundControl` (back, close, edit, flash) is **44 × 44** (was 40).
- Nav items are 60 × 51; primary buttons are full width × 46.
- Under every sticky bar (Result, Recipe detail, History) the veil is opaque where the bar
  sits, so no content reads through the button; the last list item scrolls clear of it.

## Not verified here

VoiceOver labels and focus order, Dynamic Type at the largest sizes, and reduced-motion
behaviour (the AI motion should fall back to a static state) need a coded build or a
device test: static Figma frames can't prove them.
