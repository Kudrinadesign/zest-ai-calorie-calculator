# Zest: AI Calorie Calculator

**Kudrina Design** · UX/UI trainee test task for Jito, September 2026

### Open in Figma

- ▸ **[All ten screens and the edge cases](https://www.figma.com/design/dKRU4E7vOADUMMyp4EGRbG/project?node-id=27-5)** on one canvas, page `04 · Screens & Prototype`
- ▸ **[The design system](https://www.figma.com/design/dKRU4E7vOADUMMyp4EGRbG/project?node-id=334-2785)**, page `03 · Components`: the whole library on one canvas, 37 sections grouped by family
- ▸ **[Foundations](https://www.figma.com/design/dKRU4E7vOADUMMyp4EGRbG/project?node-id=51-2)**, page `02 · Foundations`: colour, the bloom, type, spacing, radii, tokens, sizes, strokes, effects
- ▸ **[Branding](https://www.figma.com/design/dKRU4E7vOADUMMyp4EGRbG/project?node-id=234-243)**, page `01 · Branding`: the logo and five stylescapes

![Stylescape · Zest](01-branding/stylescape-zest.png)

![Zest: cover](cover.png)

Test task for the UX/UI Trainee Designer role at Jito.
Brief: [jito-dev/trainee-designer-apr-2026-test-task](https://github.com/jito-dev/trainee-designer-apr-2026-test-task) (branch `develop`).

**▶ [The design system](https://www.loom.com/share/b3507a8c96614e0297ab3a12d0332c14)** (4:00, English): the token layers, the component library and the UI they produce.
**▶ [Branding and the product, end to end](https://www.loom.com/share/7d28108c8b0049c6ba8ed49dbc445bd8)** (3:54, English): Today, the camera and what the AI reads, the result and correcting it, barcode and manual entry, Ask Zest, recipes, and the branding pages at the close.
**Figma:** [file](https://www.figma.com/design/dKRU4E7vOADUMMyp4EGRbG/project?node-id=234-243) · [prototype, Story 1, calories in a dish](https://www.figma.com/proto/dKRU4E7vOADUMMyp4EGRbG/project?node-id=28-2&scaling=scale-down&content-scaling=fixed&starting-point-node-id=28%3A2&page-id=27%3A5&show-proto-sidebar=1) · [Story 2, a recipe that fits](https://www.figma.com/proto/dKRU4E7vOADUMMyp4EGRbG/project?node-id=53-2&scaling=scale-down&content-scaling=fixed&starting-point-node-id=53%3A2&page-id=27%3A5&show-proto-sidebar=1) · all links in [`links.md`](links.md).

Everything here was produced with Claude Code driving Figma through the Figma MCP -
tokens, components, screens and prototype links are written as code and created as native
Figma nodes. Nothing was drawn by hand on the canvas.

---

## The product

**Zest** is a nutrition companion. You photograph a plate; it names what is on it, weighs
each part, and tells you what that costs your day, then says what to do next.

Both user stories from the brief are closed end to end:

| Story | Where it happens |
|---|---|
| Calculate the calories in a **dish** | Capture → Analysing → Result |
| Calculate the calories in a **specific product** | Capture → Barcode or Type it → Add a product → portion stepper |
| Find a **recipe suitable for me** | Recipes (ranked by what is left today) → Recipe detail → *Why this fits you* |

---

## The case

![The case](case.png)

| | |
|---|---|
| **Problem** | Counting calories by hand (search, weigh, type), is slow enough that people stop, and when a day goes over plan, red numbers and "you failed" make them stop faster. |
| **Hypothesis** | If logging a meal is one photo and one confirmation, and the app states facts without verdicts, people will log more of their meals and keep logging through days that go over plan. If recipes are ranked by what is left today and say why they fit, people will choose one instead of guessing. |
| **Role of AI** | It does the tedious part: names what is on the plate, estimates each portion, does the arithmetic against today's targets, suggests what fits next. The person stays in control: every estimate is "≈" and editable, nothing is logged without a tap, and when it is unsure it says how sure it is. |
| **Success metric** | North star: share of a person's meals logged per active day, at week 4. Supporting: time from camera to confirmed log; corrections per meal (should fall as Zest learns portions); days still logged after an over-budget day; recipe plans per week. These are what the product would be measured on, **not results**; nothing has been tested with users yet. |

---

## The name

The zest is the thin outer layer of a citrus: the part that holds all the flavour. That
is what the product does: it reads the surface (a photograph) and extracts what is inside
it (the macros). The mark is a round fruit with an open arc, and **the arc is the day's
remaining budget**, so the logo shows state rather than only identity.

---

## Visual direction: "Natural light"

The reference points were Milkinside's *Natural OS* work: a screen whose ground is a field
of out-of-focus light rather than a flat colour, translucent tiles with no borders and no
drop shadows, and large type set light.

One idea is ours rather than borrowed: **on Today, the colours of that field are sampled
from what the person actually ate.** The atmosphere is data, not decoration.

### Colour

| Role | Token | Value |
|---|---|---|
| Ground | `ground/porcelain` | `#EFE9E1` |
| Bloom | `bloom/plum` → `bloom/mulberry` → `bloom/ember` → `bloom/amber` | `#4A2238` `#8C3A56` `#E27A52` `#F2B585` |
| Sampled from food | `bloom/butter` | `#EDD28E` |
| **Action**: committing button, nav camera | `action/primary` | `#9E2044` burgundy |
| State (shutter, progress, eaten arc) | `accent/ember` | `#D7650E` |
| Selection (chip, radio, toggle, today's date): white text 4.9:1 | `accent/ember-strong` | `#BF540A` |
| Protein · Carbs · Fat | `macro/*` | `#4550D7` `#E6BC6A` `#CE4A34` |
| Opaque surface (nav, inputs) · suggestion tiles | `surface/raised` · `glass/peach` | `#FFFFFF` · `#F4BFA5` 66 % |
| Secondary button | `action/secondary` + `action/secondary-edge` | white with an ink 22 % edge |
| Disabled | `surface/disabled` + `ink/tertiary` | 4.1:1, readable, though disabled controls are exempt |

**The rule that keeps controls readable:** a control is never the colour of the
atmosphere. The committing action is burgundy on every screen with no exceptions and the
bloom never borrows it; ember is reserved for state and the shutter; red appears only on
destructive actions. Each macro hue also has a `-ink` twin that is safe to set text in,
because the graphic values are too light to carry type.

### Type

**Manrope**, one family, sixteen styles, each bound to the `Typography` variable collection
(family, weight, size, line height, tracking). Display sizes run Light so that large numbers
stay calm; `Metric/*` styles carry every figure.

### Layout contract

Every screen obeys the same frame: 390 × 844, 24px side margins, a 342px content column,
status bar at 0, navigation at 59, bottom bar 24 from the edge.

---

## Deliverables

| # | Deliverable | Where |
|---|---|---|
| 1 | Branding / stylescapes | Figma page `01 · Branding`: logo exploration, the main stylescape **Stylescape · Zest** (a dense collage built on one idea: the plate, the lens, the orb and the day are all circles), and four supporting 4000 × 1000 stylescapes: **Where it comes from** (the sources: peel, light, colours sampled from a real plate, photography), **Natural light** (the brand), **The plate is data** (the product), **No verdicts** (the voice). Exports in [`01-branding/`](01-branding/) |
| 2 | Design system | Figma pages `02 · Foundations` and `03 · Components` (the whole library on one canvas): 305 variables in 3 collections, 16 text styles, 8 effect styles, 51 components with all their states (41 of them variant sets) and 22 icon components. See [`docs/DESIGN-SYSTEM.md`](docs/DESIGN-SYSTEM.md) and the independent audit [`docs/DS-AUDIT.md`](docs/DS-AUDIT.md) |
| 3 | Key screens & flows | Figma page `04 · Screens & Prototype`: 10 main screens (with their prototype states), and the **Edge cases** section (9 cases + 2 sub-states), every screen built from design-system instances. Exports in [`03-screens/`](03-screens/), and [`04-edge-cases/`](04-edge-cases/) |

See [`links.md`](links.md) for the Figma link and the video walkthrough, [`docs/REVIEW-FIXES.md`](docs/REVIEW-FIXES.md) for what changed after review, [`docs/ACCESSIBILITY.md`](docs/ACCESSIBILITY.md) for the contrast check; the video script is in [`docs/VIDEO-SCRIPT.md`](docs/VIDEO-SCRIPT.md).

### Against the brief

| The brief asks for | Status |
|---|---|
| Branding / stylescapes | ✅ `01 · Branding`: 1 main collage + 4 supporting stylescapes, exports in [`01-branding/`](01-branding/) |
| Design system | ✅ 305 variables, 16 text styles, 8 effect styles, 51 components with states (41 variant sets), and 22 icons: [`docs/DESIGN-SYSTEM.md`](docs/DESIGN-SYSTEM.md), audited independently in [`docs/DS-AUDIT.md`](docs/DS-AUDIT.md) |
| Key screens / key flows, covering both user stories | ✅ Story 1 (dish **and** specific product) and Story 2 (a recipe that fits) are separate flows in the prototype and separate lanes on the flow map |
| Made with Claude Code, not by hand | ✅ Every token, component, screen and link was written as Plugin API scripts run through the Figma MCP |
| Everything in a GitHub repository | ✅ this repository |
| Accessible in incognito | ✅ Figma, the video and this repository: all checked logged out |
| Video presentation in English showing all three parts | ✅ Two walkthroughs, English: [the design system](https://www.loom.com/share/b3507a8c96614e0297ab3a12d0332c14) (4:00) and [branding and the final designs](https://www.loom.com/share/7d28108c8b0049c6ba8ed49dbc445bd8) (3:54) · script in [`docs/VIDEO-SCRIPT.md`](docs/VIDEO-SCRIPT.md) |

### Screens

Every screen is one of three kinds, and each kind always behaves the same way:

| Kind | Screens | Top-left | Bottom | Arrives by |
|---|---|---|---|---|
| **Place** | Today, Recipes, Zest, History |  | the nav | dissolve, 300 ms |
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
```

The camera in the nav always opens Capture. Every burgundy button commits something and
returns to Today, where it lands, and Today says so ("Added to breakfast · 516 kcal · Undo"). Nothing on a screen duplicates a control that already
lives in the navigation.

### The clickable scenario

Present → **Main · log breakfast → plan dinner** (starts on Today). Every step below was
clicked through in the published prototype, logged out:

1. **Today**: the Budget card's ring shows 1,056 kcal left, with protein 75 / 120, carbs
   172 / 260 and fat 38 / 80 beside it; Zest: *"Breakfast isn't logged yet."* Tap the tile.
2. **Capture** → pick the breakfast photo from the library → **Analysing** → **Result**
   (Breakfast · 09:12, 516 kcal).
3. **Add to my day** → back to **Today**. The day with the meal logged (540 kcal left,
   protein 96 / 120, carbs 210 / 260, fat 71 / 80) is a static export:
   [`03-screens/11-today-meal-added.png`](03-screens/11-today-meal-added.png).
4. **Dinners that fit** (scroll Today, or the Recipes tab) → **Recipes** → **Miso salmon**.
   The adjusted version (≈ 400 kcal, protein 30 g, fat 9 g, salmon 2 × 100 g) is a static
   export: [`03-screens/09b-recipe-detail-adjusted.png`](03-screens/09b-recipe-detail-adjusted.png).
5. **Plan for dinner** → Today: *"Dinner planned · It logs when you mark it eaten."*

Each screen carries one state in the prototype. The other states of Today and Recipe detail
are static exports in [`03-screens/`](03-screens/).

### Motion: only where the AI is working

Motion is reserved for one meaning: *the AI is doing something*. Nothing else on screen
moves, so when something does, it is always the assistant.

| Screen | What moves | What it says |
|---|---|---|
| Capture | The lens ring breathes (100 → 106 %), its halo swells a beat later, "Plate in view" rises in | It is looking |
| Analysing | A bead orbits the ring, two turns in 2.2 s; found items surface one by one; the progress bar fills | It is reading, and you can see what it has found so far |
| Ask Zest | The question, the answer and the next steps arrive in order; in the **What-if card** the pale segment of the ring (the pasta being asked about), breathes | It is answering, and showing the consequence rather than a verdict |
| Today · Result · Recipe detail · sheets | The Zest orb breathes (its *Thinking* state carries the keyframes, so every instance inherits them) | This line was written by the assistant |

Built with Figma Motion keyframes and checked frame by frame from a rendered video.

In the edge cases the lens goes dim and still whenever Zest is not reading (no plate, too
dark, offline, camera off); the orb breathes when it asks which of two dishes it is.

### Edge cases

The **Edge cases** section below the main flow covers the moments a happy path never shows:
- no food in the photo;
- two dishes that look alike;
- a dark kitchen (plus the exposed state after the flash);
- no network;
- an unknown barcode (plus the label camera);
- a day past the target;
- the first empty day;
- a corrected estimate;
- the camera turned off.

Each case keeps the rules: fact first, no verdicts, one way forward, nothing lost. Each is built only from design-system instances. See [`04-edge-cases/`](04-edge-cases/).

### Design system

- **305 variables in 3 collections:**
  - Primitives (hidden) → semantic Zest · Natural;
  - Typography.

  Every variable has a scope and code syntax.
- **16 text styles and 8 effect styles,** all bound to variables.
- **52 components with all their states** (42 of them variant sets), **and 39 icon components,** e.g.:
  - Button, Ghost button, Icon button, Chip, Toggle, Radio, Segmented control;
  - Search field, Stepper, Composer;
  - Nav bar (leading / trailing icon), Tab bar, Day / Week strip, Calendar day;
  - Day ring, Budget card, Macro stat, list rows, Bottom sheet, Snackbar;
  - Zest orb, Lens, What-if card…

  Interactive states are wired as interactive components.
- **Full reference:** [`docs/DESIGN-SYSTEM.md`](docs/DESIGN-SYSTEM.md).

---

## Tone of voice

Three rules, and they are structural rather than stylistic:

1. **Fact first, opinion second.** The number always precedes the advice.
2. **Address, then offer.** Name the person, state the observation, propose the next step.
   Never issue a verdict.
3. **Food is never bad: distribution is.** Banned: *should, bad, cheat, guilty, failed.*

Rule 3 has a visible consequence: **there is no error red anywhere in the nutrition data.**
Going over a target is stated as a fact in the brand's own clay tone.

> "Breakfast is 41% of today's fat: 33 g of 80 g.
> Lean protein at lunch keeps the rest of the day easy."

---

## Photography

All photographs are **CC0**, from the Unsplash archive on Wikimedia Commons.
- **Capture flow:** a real user photographs from above with the whole dish in view, so every photo is top-down, with the dish centred inside the scanner ring. That's also what a calorie estimate needs.
- **Recipes:** these photos are editorial, so angled shots are fine there. Credits, not required by CC0, but given -
are in [`01-branding/PHOTO-CREDITS.md`](01-branding/PHOTO-CREDITS.md).

---

## How this was made

1. Read the brief and the reference stylescapes from the task repository.
2. Agreed the brand platform and the visual direction in conversation.
3. Wrote the tokens, type ramp, components, screens and prototype links as Figma Plugin API
   scripts, executed through the Figma MCP.
4. Verified every step with a rendered screenshot before continuing: several layout bugs
   (collapsed auto-layout heights, a photo fading to a flat band, drifted top bars) were
   found this way rather than by eye at the end.

The direction changed once mid-project, from a light "Sunlit Glass" concept to the current
one. The token architecture absorbed it: changing values in one collection re-coloured
every screen at once.
