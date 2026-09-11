# Video walkthrough — script

About 6 minutes. Record the Figma file full-screen; open pages in the order below. The
brief asks to see all three parts — Branding, Design System, Final Designs — and to
explain the ideas, so each part ends on the decision behind it.

---

## 0 · Cover (20 s) — page `00 · Cover`

> Hi, I'm Sofia. This is **Zest** — an AI calorie calculator that reads your plate.
> Everything you'll see was built with Claude Code driving Figma through the MCP: tokens,
> components, screens, motion and the prototype are written as code, not drawn by hand.
> Three parts: branding, the design system, and the screens.

## 1 · Branding (1 min 30 s) — page `01 · Branding`

**Logo exploration.**
> The name: the zest is the thin outer layer of a citrus that holds all the flavour. The
> app does the same — it reads the surface, a photo, and extracts what's inside. I tried
> three marks; the fruit with an open ring won, because **the opening is the part of the
> day that's left** — the logo shows state, not just identity.

**Stylescape · Zest — the main one.**
> This is the idea everything else starts from: a collage built on one thought — the
> plate, the camera lens, the assistant's orb and the day's budget are all circles. Words
> set on a circle around a plate, one number, the live Today screen, the icons, the voice,
> a real plate sampled into the palette.

**Stylescape 00 — Where it comes from.**
> Four sources: the peel, out-of-focus light — after Milkinside's Natural OS — the colours
> already on a plate, and daylight food photography. Here I sampled the palette straight
> from a real dish: red onion is Mulberry, lentils are Amber, the roasted edge is Ember.

**Stylescapes 01–03.**
> Natural light is the brand. The plate is data is the product — one photo, a full
> breakdown. No verdicts is the voice: five words Zest will never say — should, bad,
> cheat, guilty, failed. They're built from the real screens and components, so the
> brand and the product can't drift apart.

## 2 · Design system (1 min 30 s) — pages `02 · Foundations`, `03 · Components`

> Every value is a Figma variable — about 54 of them. The screens contain no hardcoded
> colour, so when I changed the palette the whole product followed.

Point at the colour rows.
> Two rules carry the system. **Controls are never the colour of the atmosphere** — the
> committing action is burgundy on every screen, and the background never borrows it.
> And **every macro colour has a text-safe twin**, because the bar colours are too light
> to set type in.

Components page.
> The nav is four places and one verb: Today, Recipes, Zest, History — and the camera in
> the middle, which opens Capture from anywhere. Buttons: one burgundy primary per screen,
> a secondary, a danger. One detail: the secondary used to be white glass and disappeared
> on white sheets, so it now has its own token — ink at 7 %.

## 3 · Final designs (2 min 30 s) — pages `04 · Screens & Prototype`, `05 · Flow map`

**Flow map first.**
> Three kinds of screen, each with one behaviour. Places dissolve into each other. Details
> slide in from the right and have a back arrow. The capture flow rises from the bottom
> and has a close button. And every burgundy button ends on Today, where the meal lands.

**Play the prototype** (Present → "Zest · full journey").
1. Welcome → *Scan my first meal* → **Capture**.
   > The lens breathes — motion only ever means the AI is working.
2. Shutter → **Analysing**.
   > A bead orbits the ring while it reads, and each item appears as it's found — you can
   > see the AI's work.
3. Auto → **Result** → *Add to my day* → **Today** with *Added to breakfast · 516 kcal · Undo*.
   > First story: calories in a dish. Every weight is marked as an estimate, every
   > percentage is computed from the same targets as Today — protein 21 of 120 g is 18 %.
   > Tap a line and you correct it; the meal lands on Today and Today says so.
4. Camera → *Type it* → **Add a product** → stepper.
   > Second half of story one: a specific product.
5. Today → *Dinners that fit* → **Recipes** → **Recipe detail** — *Why this fits you*.
   > Story two: a recipe that suits me — ranked by what's left today, and it says why —
   > including the trade-off: this one takes fat 5 g past the target, so Zest says so and
   > suggests halving the sesame oil. Planning dinner and logging it are separate actions.
6. **Ask Zest**.
   > The assistant does the arithmetic, not the person.

**Edge cases** (Present → the `Edge · …` flows, or scroll to the second row).
> A happy path only shows what goes right. Nine screens for what doesn't: no plate in the
> photo, two dishes that look alike — with how sure it is — a dark kitchen, no network,
> an unknown barcode, a day over budget, the first empty day, a corrected estimate, and
> the camera switched off.
> Same rules everywhere: fact first, no verdicts, one way forward, nothing lost. My
> favourite is the first day — the background is sampled from what you ate, so with
> nothing eaten it's almost colourless.

## Close (15 s)

> The repository has every export, the reasoning, and the Figma link. Thanks for
> watching.
