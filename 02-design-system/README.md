# Design system

| File | Figma page | What it shows |
|---|---|---|
| `components.png` | 03 · Components | Overview: how tokens, components and state fit together, and an index of the family pages |
| `foundations.png` | 02 · Foundations | Colour, the bloom, typography, spacing and radius, token architecture, sizes and strokes, effects |
| `03.1-icons.png` | 03.1 · Icons | 39 Lucide icons as components (stroke and colour from variables) |
| `03.2-actions.png` | 03.2 · Actions | Button, Ghost button, Icon button, Chip, Shutter & Library, with every state |
| `03.3-inputs-and-selection.png` | 03.3 · Inputs & selection | Toggle, Radio, Step indicator, Segmented control, Stepper, Search field, Composer |
| `03.4-navigation.png` | 03.4 · Navigation | Status bar, Nav bar, Tab bar, Day / Week strip, Calendar day |
| `03.5-data-display.png` | 03.5 · Data display | Macro bar, Macro stat, Tag, Bullet, Badge / Tile head, Day ring, list rows |
| `03.6-cards-and-surfaces.png` | 03.6 · Cards & surfaces | Budget card, Today tiles, Recipe card, Snackbar, Bottom sheet, Notice card |
| `03.7-feedback-and-ai.png` | 03.7 · Feedback & AI | Zest orb, Insight card, Chat bubble, Status pill, Lens, What-if card |

The full reference is in [`docs/DESIGN-SYSTEM.md`](../docs/DESIGN-SYSTEM.md). The totals:
- 354 variables in 5 collections (Primitives → semantic, Typography, two Prototype collections);
- 16 text styles and 8 effect styles, all bound to variables;
- 64 components, each with its states.

## The rules worth knowing

**One primary button per screen.** It sits at the bottom, full width, and commits something.
Sticky buttons sit on an opaque veil and never cover content.

**Four places and one verb.** The tab bar holds Today · Recipes · Zest · History. The camera
in the middle is the verb.

**`‹` and `×` mean different things.** `‹` goes one step back. `×` leaves a flow without saving.

**Controls are never the colour of the atmosphere.** The bloom never borrows
`action/primary`. Selection is always `accent/ember-strong` with white text. Red appears only
on destructive actions and never on food data.

**Every macro hue has a text-safe twin.** `macro/protein` is for bars, `macro/protein-ink`
for the number beside it, and `macro/protein-soft` for the "with this meal" part of a
What-if bar.

**Motion means the AI is working.** Nothing else moves:
- the lens breathes while it looks, and a bead orbits while it reads;
- the Zest orb breathes in its Thinking state;
- the What-if ring pulses the meal being asked about.

When the AI is stuck (no connection, too dark), the lens goes dim and still.
