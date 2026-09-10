# Zest — Design Spec

**Date:** 2026-09-10
**Context:** Test task for UX/UI Trainee Designer — `jito-dev/trainee-designer-apr-2026-test-task` (branch `develop`)
**Language of all deliverables:** English (required by the task)

---

## 1. The task, restated

Show the key mobile screens of a **Calories Calculator** app covering two user stories:

- **US-A** — As a user, I want to calculate the amount of calories in a dish or a specific product.
- **US-B** — As a user, I want to find a recipe for a dish that is suitable for me.

Three graded deliverables: **Branding / Stylescape**, **Design System**, **Key Screens / Flows**.
Everything must live in a public GitHub repo, be reachable from incognito, be in English, and be walked through in a recorded video.

**The grading subtext matters as much as the artefacts.** The task explicitly says: *"We do not expect, and moreover want to exclude, manual work as much as possible"* and *"fully manual work created by hand in Figma"*. The process is being judged. Everything below is therefore generated as code and pushed into Figma programmatically — Figma is the presentation surface, not the drawing tool.

---

## 2. Brand platform

### 2.1 Name

**Zest.**

The zest is the thin outer layer of a citrus fruit — the part that holds all the flavour. That is exactly what the product does: **it reads the surface (a photo of a plate) and extracts what is inside it (the macros).**

The metaphor pays off three times, which is why it was chosen over more literal candidates:

1. It names the product.
2. It names the assistant persona in the UI ("Zest").
3. It generates the brand mark — a citrus segment `◕`, which doubles as the camera reticle and the loading indicator.

### 2.2 Positioning

> Zest is an AI nutrition companion that turns a photo of your plate into precise numbers — and one respectful sentence telling you what to do next.

### 2.3 Tone of voice — three rules

These are design constraints, not copy suggestions. They are enforced in the component library.

**Rule 1 — Fact first, opinion second.** The number always precedes the advice. The user sees data before they see a judgement of the data.

**Rule 2 — Address, then offer.** Use the person's name, state the observation, propose the next action. Never issue a verdict.

> "Good morning, Dmitry. This breakfast covers 80% of your fat budget — let's build lunch around protein."

**Rule 3 — Food is never bad; distribution is.** Banned vocabulary: *should, bad, cheat, guilty, failed, naughty, sinful.* Going over a target is described in neutral, factual language and rendered in the brand's own deep coral, never in an error red.

Rule 3 has a direct visual consequence and is the strongest thing to demonstrate on video: **the design system has no error-red for nutrition data.** Over-budget states use `coral-deep`, the same family as the brand colour. A design decision that falls out of a copy rule is evidence of a system, not a mood board.

---

## 3. Visual direction — "Sunlit Glass"

Daylight through a kitchen window, falling on glassware. Warm, airy, soft-shadowed. Glass is used because the product's core act is *seeing through* something to what it contains — the same idea as the name.

### 3.1 Colour tokens

Light theme is the only theme in scope. Dark theme is explicitly out of scope for this task.

| Token | Value | Use |
|---|---|---|
| `surface/canvas` | `#FAF7F2` | app background |
| `surface/raised` | `#FFFFFF` | opaque cards |
| `surface/sun` | radial `#FFE9C9` → `#FAF7F2` | ambient backdrop behind glass |
| `glass/fill` | `rgba(255,255,255,.55)` | standard glass card |
| `glass/fill-strong` | `rgba(255,255,255,.72)` | sheets, overlays |
| `glass/border` | `rgba(255,255,255,.70)` | 1px top-lit edge |
| `brand/coral` | `#FF7A45` | brand fills, graphics, primary button |
| `brand/coral-deep` | `#C4441A` | accent **text**, links, over-budget |
| `brand/coral-tint` | `#FFE7DC` | selected chip, subtle fill |
| `macro/protein` | `#4CC38A` | graphics |
| `macro/protein-deep` | `#1E8B5C` | protein text/labels |
| `macro/carbs` | `#FFB020` | graphics |
| `macro/carbs-deep` | `#8A5A00` | carbs text/labels |
| `macro/fat` | `#FF7A45` | graphics (= brand coral) |
| `macro/fat-deep` | `#C4441A` | fat text/labels |
| `text/primary` | `#1A1A1A` | body, headings |
| `text/secondary` | `#6B6760` | supporting text |
| `text/tertiary` | `#8A867E` | disabled, decorative only |

**Accessibility reasoning (to be shown in the design system, not hidden).**
Bright coral cannot carry text on a light background, so the system splits each hue into a *graphic* value and a *deep* text value:

- Primary button = `brand/coral` fill with `text/primary` (ink) label → ≈ 6:1. Dark-on-warm-coral is also the more distinctive choice, and it is the one the system commits to.
- `brand/coral-deep` on `surface/canvas` → ≈ 6.3:1 ✓
- `text/secondary` `#6B6760` on canvas → ≈ 4.7:1 ✓ (a naive `#7A7670` would have failed at 3.9:1)
- `text/tertiary` → ≈ 3:1, permitted for disabled and decorative text only

Every `-deep` pair must be verified against WCAG AA before the system is published. See §8.

### 3.2 Typography

**Fraunces** (display) + **Inter** (interface). Both from Google Fonts — free, embeddable in the repo, available in Figma, and reachable from incognito.

Fraunces is a soft optical serif with `SOFT` and `WONK` axes; at display sizes it produces the warmth the direction needs without becoming decorative. Inter carries the interface and, critically, provides **tabular figures** — every calorie and gram readout uses `tnum` so numbers do not shift as they animate.

| Style | Font | Size / line | Weight |
|---|---|---|---|
| Hero number | Fraunces | 72 / 72 | 600, opsz 144, SOFT 100 |
| H1 | Fraunces | 34 / 40 | 600 |
| H2 | Fraunces | 26 / 32 | 600 |
| H3 | Inter | 20 / 28 | 600 |
| Body L | Inter | 17 / 26 | 400 |
| Body | Inter | 15 / 22 | 400 |
| Label | Inter | 13 / 18 | 500 |
| Caption | Inter | 12 / 16 | 500, +2% tracking, uppercase |

### 3.3 Form

- **Spacing** — 4pt base: 4, 8, 12, 16, 20, 24, 32, 40, 56, 72
- **Radius** — sm 12, md 20, lg 28, xl 36, full 999
- **Elevation** — warm shadows, never neutral grey:
  - `e1` `0 2px 8px rgba(122,74,45,.06)`
  - `e2` `0 8px 24px rgba(122,74,45,.08)`
  - `e3` `0 20px 48px rgba(122,74,45,.12)`
- **Glass recipe** — `glass/fill` + background blur 30 + 1px `glass/border` top-lit edge + `e2`. Sheets use blur 44 and `glass/fill-strong`; chips and bars use blur 18.
- **Frame** — 390 × 844 (iPhone 14/15). 20px side margins, 4 columns, 12 gutter. Safe areas 59 top / 34 bottom.

### 3.4 The signature device — "the scan"

A citrus-segment reticle with a soft light sweep passing across it.

One shape, four jobs: **brand mark** → **camera reticle** → **loading indicator** → **stylescape motif**. Reusing a single form across brand, product and marketing is the clearest available evidence that this is a system rather than a set of screens.

### 3.5 Photography

Overhead plates, daylight, soft single-direction shadow, real food, no glossy retouching. Sourced from Unsplash under its free licence; sources credited in the repo README.

---

## 4. Screens

Twelve screens (six in Flow A, three in Flow B, three supporting). Both user stories are traceable end to end; nothing beyond that is designed, per YAGNI and per the task's own note that perfect work is not expected.

### Flow A — Calculate calories (US-A)

| # | Screen | Purpose |
|---|---|---|
| S03 | **Today** | Daily kcal ring, macro bars, meal timeline, Zest message card. The home surface. |
| S04 | **Capture** | Camera with the citrus reticle. Manual-entry and barcode entry points. |
| S05 | **Analyzing** | Glass overlay; detected items surface one by one. Makes the AI act legible instead of a spinner. |
| S06 | **Result / Breakdown** | Detected ingredients with editable grammage, per-item kcal, macro total, Zest's sentence, "Add to day". |
| S07 | **Edit portion** (sheet) | Stepper + unit switch. The correction path — proves the AI is treated as fallible. |
| S08 | **Search product** | Search + barcode result, product card with portion stepper. **This is what satisfies "or a specific product" in US-A.** |

### Flow B — Find a recipe (US-B)

| # | Screen | Purpose |
|---|---|---|
| S09 | **Recipes** | Feed ranked by what fits the day's remaining budget. Filter chips. |
| S10 | **Recipe detail** | Per-serving macros, ingredients, steps, and a **"Why this fits you"** block from Zest. **This is what satisfies "suitable for me" in US-B** — the word *suitable* is the whole story, so it gets an explicit component. |
| S11 | **Filters** (sheet) | Diet, time, remaining-budget fit, ingredients on hand. |

### Supporting

| # | Screen | Purpose |
|---|---|---|
| S01 | **Onboarding — Goal** | Goal, activity, targets. |
| S02 | **Onboarding — Your numbers** | Computed targets + Zest's introduction, which establishes the tone of voice on first contact. |
| S12 | **Profile & goals** | Targets, tone, units. |

---

## 5. Design system inventory

Built as Figma variables + components, generated programmatically.

**Foundations:** colour tokens, type styles, spacing scale, radius scale, elevation styles, glass recipes, grid, iconography, the scan device, tone-of-voice rules page.

**Components:**

1. `GlassCard` — default / elevated / inset
2. `MacroRing` — kcal donut, three segments, over-budget state
3. `MacroBar` — label, value, track
4. `MacroTriplet` — P / F / C row
5. `Button` — primary / secondary glass / ghost · L, M, S · default, pressed, disabled
6. `Chip` — default / selected / with count
7. `SearchField` — idle, focused, filled
8. `Stepper` — portion in g / ml / pieces
9. `FoodRow` — thumbnail, name, portion, kcal, macro dots
10. `RecipeCard` — image, title, kcal per serving, fit badge
11. `ZestMessage` — mark, message, optional action. **Enforces the tone rules: fact slot before advice slot.**
12. `NavBar` — title, back, action
13. `TabBar` — Today · Recipes · Add ⊕ · Insights · Profile
14. `BottomSheet` — grabber, header, content
15. `ScanReticle` — idle, scanning, locked
16. `FitBadge` — "Fits your day" / "320 kcal left" / over-budget
17. `Avatar`
18. `DayTimeline` — meal strip

`ZestMessage` is the component that carries the brand. It has two required text slots — observation and action — so a copy rule becomes structurally impossible to break.

---

## 6. Production approach

The pipeline is the deliverable as much as the pixels are.

1. **Generate as code.** Every artefact — stylescape, token sheet, component sheet, all twelve screens — is authored as HTML/CSS at 390 × 844 (and one wide canvas for the stylescape), rendered locally, and reviewed as images.
2. **Push into Figma via the Figma MCP.** Variables, component sets and frames are created as native Figma nodes with auto-layout and bound variables — not pasted screenshots. Built incrementally, section by section, because large single writes are slow and fragile.
3. **Publish.** Figma file set to view-access-by-link; repo contains the links file.

**Figma file structure**

```
00  Cover
01  Branding / Stylescape
02  Design System — Foundations
03  Design System — Components
04  Screens · Flow A — Calculate
05  Screens · Flow B — Recipes
06  Flows (connected)
```

**Repository structure**

```
README.md            project, rationale, links, photo credits
01-branding/         stylescape, logo, palette, tone of voice
02-design-system/    tokens, components, documentation
03-screens/          both flows
links.md             Figma link (link-access verified) + video link
```

### Known risks

- **Background blur in Figma** is an effect, not a CSS property; the glass recipe must be re-expressed as Figma's *Background blur* effect. Verify on the first component before building the rest.
- **Fraunces variable axes** (`SOFT`, `WONK`) may only be available as static instances in Figma. Verify early; fall back to the nearest static cut and record the substitution.
- **Figma MCP write throughput** — build page by page and verify each before continuing.
- **Photo licensing** — Unsplash only, credited. No stock that cannot be viewed in incognito.

---

## 7. Out of scope

Dark theme · tablet and web layouts · settings beyond goals and units · social and sharing features · water and exercise tracking · real API or data model · production-ready code. The task asks for key screens; anything past that dilutes the review.

---

## 8. Verification checklist

Design work has no test suite, so completion is defined by this checklist. Each item is checked with evidence before the work is called done.

1. **Contrast** — every text/background pair audited against WCAG AA; every `-deep` token measured, not assumed.
2. **Fit** — every screen renders correctly at 390px with no horizontal overflow and correct safe areas.
3. **Token coverage** — no hardcoded colour, size, radius or shadow in any screen; every value resolves to a variable.
4. **Story traceability** — US-A demonstrably closed by S04→S06 *and* S08; US-B demonstrably closed by S09→S10.
5. **Copy audit** — all text in English; zero occurrences of the Rule 3 banned vocabulary; every `ZestMessage` has both slots filled.
6. **No error-red** — confirm no red outside the brand coral family appears in any nutrition state.
7. **Access** — Figma link and repo both opened in a real incognito window and confirmed to load.
8. **Video coverage** — the recording visibly shows all three parts: branding, design system, screens.
