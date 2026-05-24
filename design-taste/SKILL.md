---
name: design-taste
description: |
  A taste-engine for any visual artifact — Instagram carrousels,
  landing pages, SaaS dashboards, components, posters, pitch decks,
  emails, social statics, and more. Format-class-first routing: the
  brief is classified by *what shape* it is before *what aesthetic*.
  Each format class holds a curated set of specimens (real-world
  reference designs decomposed into reusable rules). The skill picks
  the right specimen, applies universal craft rules (typography,
  color, motion, anti-AI-slop, laws of UX, state coverage), then
  self-critiques on five dimensions before emitting. Use whenever the
  brief asks for a UI mockup, web prototype, slide deck, social
  carrousel, dashboard, marketing page, poster, email, "make this
  look better", "design review", or any output where visual craft
  matters.
---

# Design Taste Skill 🎨 — v3.1

A skill that produces work with **shipped-product taste** — not LLM
default output. Two-step routing: classify the brief by *format*,
then pick a *specimen* from that format class. Apply universal craft
rules. Self-critique. Emit.

## 🧭 The routing protocol (read this first)

The arc is fixed: **discovery → routing → planning → execution →
critique → emission.** The user is paying attention to *speed of
feedback*; obeying this arc is what makes the skill feel responsive
instead of stuck. Steps cannot be skipped on a fresh brief.

### Step 0 — Discovery (turn 1 always emits a brief-lock form)

On a **fresh design brief**, your very first output is one short prose
line + a single block of clarifying questions. Nothing else. No file
reads. No CSS. No "I'll get started." The form is your time-to-first-byte.

Emit this as a fenced markdown block titled **"Brief lock — 30 seconds"**
with 5–7 questions, single-select where possible. Tailor the questions
to the brief — drop ones the user already answered, add fields the
brief uniquely needs.

````
**Brief lock — 30 seconds.** I'll lock these in before building.
Skip what doesn't apply — I'll fill defaults.

1. **What are we making?** (Carrousel / Landing / Dashboard / Component / Poster / Deck / Email / Social)
2. **Primary surface?** (Mobile / Desktop / Both / Fixed canvas — give dimensions)
3. **Who is this for?** (one line — e.g. "early-stage investors", "dev-twitter", "internal exec review")
4. **Visual tone?** (pick up to 2: editorial / minimal / brutalist / friendly / luxury / playful / utility)
5. **Brand context?**
   a. *Pick a direction for me* — I'll route to a specimen or use the direction library
   b. *I have a brand spec / reference site / screenshot* — I'll extract it
   c. *Specific specimen* — name it (e.g. "Linear-style", "Bauhaus poster")
6. **Roughly how much?** (e.g. "8 slides", "1 landing + 3 sub-pages", "4 mobile screens")
7. **Anything to avoid?** (fonts, colors, references, deadlines)
````

**Hard rules for the form:**
- Fresh brief = always emit. A *detailed* brief still leaves visual tone /
  color / scale open — exactly what the form locks. Don't justify
  skipping it ("the brief is rich enough"). Ask anyway.
- After the form, **stop your turn.** Wait for answers. Do not narrate
  "I'll wait" or pre-emptively start work.
- **Only skip the form** in three narrow cases:
  - User is replying *inside an active design* with a tweak ("make the
    headline bigger", "swap slide 3 image").
  - User explicitly says "skip questions" / "just build" / "no questions".
  - User's message opens with `[brief locked — ...]` or pre-supplied
    answers in the same shape as the form fields.
  - Brief already answers ≥4 of 7 fields — emit a condensed confirmation
    (restate what you inferred, ask only the open fields) rather than
    the full form.

### Step 1 — Format classification

What *shape* is the artifact? The format determines the canvas, the
viewing context, and the constraints. A landing page and a carrousel
look superficially similar but obey different rules — fold vs swipe,
hover vs tap, performance budget vs single-frame-render.

The board (`references/board.md`) currently holds these classes:

| Class | When to pick |
|---|---|
| 📱 Instagram Carrousel | vertical 1080×1350, swipe nav, deck-shaped social post |
| 🌐 Website Landing Page | desktop 1440px+ with mobile collapse, fold matters, conversion-driven |
| 🎛️ SaaS Dashboard | application UI, dense data, sustained-use surface |
| 🧱 Component / UI Mockup | single component or screen showcase |
| 🪧 Poster / Print | single-image artifact, no scroll, no interaction |
| 📊 Pitch Deck / Slides | 16:9 or 9:16, 8–15 slides, presented or shared |
| 📧 Email / Newsletter | inbox-rendered, 600–640px, table-based for Outlook |
| 📸 Social Static | single-frame post (square 1080×1080 or landscape 1200×630) |

If the brief explicitly names the format ("landing page", "carrousel",
"poster"), skip to Step 2. If it's ambiguous, **ask the user one
question** (single-select, not free text) before continuing.

Examples of ambiguity worth asking about:
- "design something for Booksmark AI" — landing? dashboard? mobile screen?
- "post about our Series A" — carrousel? social-static? pitch deck?
- "weekly update" — newsletter? Slack message? deck?

### Step 2 — Specimen selection within class

Each class in `references/board.md` lists 2–4 specimens with full
decompositions and a per-class disambiguator table. Read the table.

**Routing branches on the `brand context` answer from Step 0:**

#### Branch A — "Pick a direction for me"

1. **Try the board first.** If the brief's tone signal + class points
   clearly to one specimen, use it.
2. **If no specimen quite fits** (rare — usually means the brief is
   unusual), fall back to `references/directions.md`. Pick one of the
   5 deterministic directions, bind its palette + font stacks
   **verbatim** into the artifact's `:root`. Do not improvise palette
   values.
3. State the routing rationale in one sentence ("picking
   `linear-app-saas` because the audience is dev-twitter and the
   performance budget is tight"), then proceed.

#### Branch B — "I have a brand spec / reference site / screenshot"

Run brand-spec extraction *before* planning sections — five steps:

1. **Locate the source.** If files attached, list them. If a URL,
   request `<brand>.com/brand`, `<brand>.com/press`, `<brand>.com/about`,
   inspect the landing page CSS.
2. **Download styling artefacts.** Their CSS, brand-guide PDF,
   screenshots — whatever's available. Read what they ship; don't
   infer from the homepage screenshot alone.
3. **Extract real values.** `grep -E '#[0-9a-fA-F]{3,8}'` on the CSS
   for hex, eyeball screenshots for typography. **Never guess colors
   from memory** — "I think Linear uses purple" is a P0 routing
   failure.
4. **Codify a one-shot DESIGN.md** with six tokens (`--bg --surface
   --fg --muted --border --accent`) in OKLch + display/body/mono font
   stacks + 3–5 posture rules you observed (radii, border weight,
   accent budget).
5. **Vocalise the system** in one sentence so the user can redirect
   cheaply ("warm cream background, single rust accent at
   `oklch(58% 0.15 35)`, Newsreader display + system body — confirm
   before I proceed?").

#### Branch C — "Specific specimen named"

If the brief explicitly names a specimen on the board → use it
directly, skip the disambiguator.

If the brief names a specimen **not yet on the board** ("BMW
Motorsport-style", "Nothing Phone-style") → flag the gap honestly,
propose the closest neighbor, and offer to draft a one-shot custom
DESIGN.md per § *Custom specimen / new format class* below.

#### Mixed-signal cases

If disambiguator signals are mixed → propose the top 2 with their
tradeoffs and ask the user to pick. Don't guess routing on a coinflip.

### Step 3 — Plan the section list (and read assets BEFORE writing CSS)

Two things happen here, in order:

1. **State the section list** in one sentence to the user
   ("hero → 3-feature split → testimonial wall → pricing 2-tier →
   footer"). Apply Hick's / Pareto / Choice Overload — the user
   redirects cheaply now, not after 200 lines of HTML.
2. **Pre-flight the assets.** Every specimen on the board has a
   decomposition listing substrate, display/body fonts, accents,
   components, and banned patterns. **Re-read the chosen specimen's
   block before writing any CSS** — even if you "remember" it. The
   single biggest reason ad-hoc output looks worse than specimen-
   bound output is that the agent re-derived defaults instead of
   reading them.

If a specimen ships explicit CSS tokens or component primitives
(e.g. `editorial-technical` ships `--claude-glow`, `.rail`, `.bus`,
`.pillar`), bind them verbatim. Do not improvise tokens that the
specimen has already declared.

### Step 4 — Apply universal craft rules

These ride on top of *any* specimen. They're the difference between
shipped-product output and LLM-default output. Full details in
`references/craft.md`; the must-know minimums are inline below.

### Step 5 — Self-critique before emitting

Run the 5-dimension review. If 2+ dimensions land below 6, rework
before showing the user. Full workflow in `references/critique.md`.

### Step 6 — Emit

Single-file HTML by default, between `<artifact>` tags. One sentence
before, **stop after `</artifact>`** — don't paraphrase the artifact
in chat.

## 🎯 Mission

Most AI-generated UI fails for the same reasons: indigo accent,
two-stop gradients, emoji feature icons, ALL CAPS without tracking,
the standard Hero → Features → Pricing → CTA template skeleton, and
zero awareness that a carrousel obeys different rules than a landing
page. This skill removes those failure modes by routing on format
first, applying tested specimens second, and self-critiquing third.

**The ratio that produces taste:** ~80% proven patterns + ~20%
distinctive choice. The 20% lives in exactly one of:

- One bold visual move — a typography choice, a single color decision, an unexpected proportion.
- Voice and microcopy — a button that says "Start tracking" beats one that says "Get started".
- One micro-interaction the user will remember — a button press that moves 2px, a number that counts up.
- One detail only someone who used the product would put there — a kbd shortcut hint, a status badge with product-specific phrasing.

Pick one. Not five. The rest stays conventional.

If a reviewer screenshots the artifact and someone outside the
project can identify the product, you have soul. If not, you shipped
a template.

## 🔧 Universal craft rules (must-know minimums)

### Typography

```
Letter-spacing      | Context
--------------------|----------------------------------------
0                   | Body 14–18px (default)
+0.01 to +0.02em    | Small 11–13px
+0.02em             | UI labels, button text
+0.06 to +0.10em    | ALL CAPS — REQUIRED, NO EXCEPTIONS
0 to -0.01em        | Subheadings H2/H3 20–31px (Emphasize weight)
-0.01 to -0.02em    | Headings H1 32px+
-0.02 to -0.03em    | Display 48px+
```

**ALL CAPS without `≥0.06em` tracking is the single most reliable
AI-slop tell.** Display text without negative tracking is the second.

Three-weight system: **Read** (400/450) for body, **Emphasize**
(510/550) for UI/labels, **Announce** (590/600) for headlines/buttons.

Cap at **6–8 type sizes per artifact**, **2 typefaces max**, **50–75
characters per line** (`max-width: 65ch`). Body in `text-align:
justify` is banned (rivers).

Full rules in `references/craft.md`.

### Color

Color rules are **specimen-scoped**, not universal. The default
discipline is *one accent, ≤2 visible uses per screen* — but specimens
like `higgsfield-friendly-editorial` deliberately use two accents
(terracotta + chartreuse) as a signature, and `bauhaus-geometric`
uses 3–4 primaries as the whole point. Read the chosen specimen's
accent rule before writing CSS.

**Pixel-share allocation** (apply on top of the specimen's accent
rule — the *amount* of each layer is universal, the *hues* are
specimen-scoped):

| Layer | Share of pixels | Tokens |
|---|---|---|
| **Neutrals** | 70–90% | `--bg`, `--surface`, `--fg`, `--muted`, `--border` |
| **Accent** (one — never invent a second) | 5–10% | `--accent` only |
| **Semantic** | 0–5% | `--success`, `--warn`, `--danger` |
| **Effect** (gradients, glows) | <1% | rarely justified |

Plan all four layers *before* writing any CSS. If you can't articulate
which token will fill 70%+ of pixels, you don't have a palette — you
have a mood board.

What IS universal:
- Never pure `#000000` or `#FFFFFF`. Backgrounds: `#0F0F0F` dark or
  `#FAFAFA` light. Foregrounds: `#F0F0F0` dark or `#111111` light.
  On dark surfaces, prefer `1px rgba(255,255,255,0.08)` borders over
  solid dark borders. Specimen DESIGN.md tokens override these
  baselines with OKLCH-tinted values — that's intentional.
- Contrast minimums: **4.5:1** body text, **3:1** large text and UI
  components.
- Semantic naming: name tokens by *purpose* (`--accent`, `--success`)
  not by hue (`--blue-500`).
- Indigo `#6366f1` and the Tailwind-default purple→blue gradient are
  banned globally regardless of specimen — they are the textbook AI
  tells.

### Motion

| Duration | Use |
|---|---|
| 50–100ms | Instant feedback (press, toggle, hover) |
| 150ms | Default for state-confirmation |
| 200–300ms | Entering UI (modals, sheets, dropdowns) |
| 300–500ms | Cross-screen transitions, container morphs |
| >500ms | Reserved for cross-screen / staged only |

Animate when the user is moving through space, time, or state. Don't
animate to teach, decorate, signal "premium", or fill silence. Curves
for opacity/color, springs for position/scale/rotation.

Default easing: M3 standard `cubic-bezier(0.2, 0, 0, 1)` (front-loaded,
not the M2 symmetric `cubic-bezier(0.4, 0, 0.2, 1)`).

Every transform-based animation must respect
`@media (prefers-reduced-motion: reduce)` — strip translate/scale/rotate,
keep opacity crossfades.

### Stateful UI (for any data-bearing surface)

Every surface that fetches, transforms, or accepts data must render
**five states**: Loading, Empty, Error, Populated, Edge. Forms add
three: Untouched, Dirty-Valid, Submitted-Pending.

Validate **on blur**, not on first keystroke. Errors must answer:
what happened, why if knowable, what the user can do — and preserve
user input across failure.

Full state-coverage rules in `references/craft.md`.

## 🚫 The seven cardinal sins (universal P0 fails)

These are P0 failures regardless of specimen. Any one of them =
artifact regression.

1. **Default Tailwind indigo as accent** — `#6366f1`, `#4f46e5`,
   `#4338ca`, `#3730a3`, `#8b5cf6`, `#7c3aed`, `#a855f7`. The
   textbook AI tell. The specimen's DESIGN.md provides `--accent`; use it.
2. **Two-stop "trust" gradient on the hero** — purple→blue,
   blue→cyan, indigo→pink. A flat surface + intentional type beats
   this every time.
3. **Emoji as feature icons** — `✨ 🚀 🎯 ⚡ 🔥 💡` inside `<h*>`,
   `<button>`, `<li>`, or `class*="icon"`. Use 1.6–1.8px-stroke
   monoline SVG with `currentColor`. (Specimens with explicit sticker
   systems like `higgsfield-friendly-editorial` have a scoped
   exception — but stickers are header signatures, not feature
   icons.)
4. **Sans-serif on display when the specimen binds a serif** — H1/H2
   must respect the specimen's display family.
5. **Rounded card with a colored left-border accent** — the
   canonical "AI dashboard tile" shape. Drop either the radius or
   the left border.
6. **Invented metrics** — "10× faster", "99.9% uptime", "3× more
   productive". Pull from real source or use a labelled placeholder.
7. **Filler copy** — `lorem ipsum`, `feature one / two / three`.
   Empty sections are composition problems, not word problems.

## ⚠️ Soft tells (P1 — should fix)

Not regressions, but signals a reviewer will notice. Fix before
shipping when the brief allows it.

- **Standard "Hero → Features → Pricing → FAQ → CTA" skeleton with no
  variation** — the AI-template default. Introduce at least one
  unconventional section (testimonial wall as full-bleed quote,
  pricing as comparison-against-status-quo, an inline mini-product-demo).
- **External placeholder image CDNs** (`unsplash.com`, `placehold.co`,
  `picsum.photos`). Fragile and obvious. Use an inline SVG placeholder
  or a labelled `[image: description]` block instead.
- **More than ~12 raw hex values outside `:root`** — tokens were not
  honoured. Move to CSS custom properties.
- **`var(--accent)` visible more than twice per screen.** Cap at 2.

## 🔎 Second-order reflex check

Passing the seven sins is necessary, not sufficient. Run this before
emitting:

**First-order:** Can someone guess the theme + palette from the product
category alone ("observability → dark blue", "healthcare → white + teal",
"fintech → navy + gold")? If yes, you're in the first training-data
reflex. Rework the scene sentence and color strategy until the answer
is no longer obvious from the domain.

**Second-order:** Can someone guess the aesthetic family from category +
anti-references ("AI workflow tool that's not SaaS-cream →
editorial-typographic", "fintech that's not navy-and-gold →
terminal-native dark mode")? If yes, you avoided the first reflex and
landed in the one beneath it. Rework until both answers are
non-obvious.

Soul-test shortcut: can you name a specific shipped product this artifact
could pass for? If yes → soul. If you can only name an aesthetic
school → you're still in a reflex.

## 📐 Composition with named UX laws

Picking a section list is upstream of writing CSS. The Laws of UX
tell you which sections earn their place.

- **Hick's Law** — cap any decision-screen at 3–5 visible primary
  options.
- **Choice Overload** — pricing 3–4 tiers (one recommended); product
  grids 6–9 cards above fold; settings ≤5 named groups.
- **Anchoring** — place the recommended pricing tier where it
  anchors comparison; pre-select safer defaults.
- **Pareto / 80-20** — find the 2–3 actions that drive the dominant
  journey; emphasize visually; demote the rest.
- **Selective Attention** — reserve the strongest contrast for the
  *single* goal-relevant action per surface.
- **Von Restorff** — the item that differs is the one remembered.
  Make the recommended tier visually distinct, paired with a
  non-color signal.
- **Jakob's Law** — reuse category convention. Novelty must earn its
  keep.
- **Goal-Gradient + Zeigarnik** — visible progress ("3 of 5 steps")
  pulls toward completion. Reserve for genuinely beneficial flows.
- **Peak-End Rule** — the success state at the *end* of a flow
  earns a high-effort celebration.

Full inventory + primary sources in `references/laws-of-ux.md`.

## 🔍 Self-critique (5 dimensions)

Run before showing output. Score each dimension 0–10 with **evidence**
— cite a specific element, class, or section.

| # | Dimension | What it asks |
|---|---|---|
| 1 | **Philosophy consistency** | Does every micro-decision argue for the same thesis? |
| 2 | **Visual hierarchy** | Can a stranger figure out what to read first, second, third? |
| 3 | **Detail execution** | Alignment, leading, kerning, edge-case spacing — the 90/10 stuff. |
| 4 | **Functionality** | Does it *work* for its intended use? CTA above fold, mobile reflow, all five UI states present? |
| 5 | **Innovation** | Is there one element that makes people lean in? |

Bands: 0–4 broken · 5–6 functional · 7–8 strong · 9–10 exceptional.

Don't grade-inflate. Mean above 8 across all 5 is suspicious. If 2+
dimensions land below 6, **rework before emitting** — don't ship a 4
hoping the user won't notice. Full workflow in
`references/critique.md`.

## 📋 Custom specimen / new format class

If the brief names a real brand or aesthetic not on the board (e.g.
"BMW Motorsport-style", "Nothing Phone-style", "Studio Ghibli
poster"), and none of the board specimens fit:

1. **Flag the gap honestly** — "no specimen on the board for
   {request}; closest neighbors are {A} and {B}".
2. **Offer two paths:** (a) propose the closest neighbor with
   modifications, (b) draft a one-shot custom 9-section DESIGN.md
   inline before writing CSS.
3. **Suggest logging the new specimen** for future curation if the
   user is happy with the result — the board grows by accumulation.

The 9-section custom DESIGN.md schema:

1. **Visual Theme & Atmosphere** — one paragraph capturing mood.
2. **Color Palette & Roles** — `--bg --surface --fg --muted --border
   --accent` plus semantics, named by purpose.
3. **Typography Rules** — display + body fonts, scale, line-heights,
   letter-spacing per size band.
4. **Component Stylings** — buttons, cards, inputs, links: radius,
   padding, focus state.
5. **Layout Principles** — grid, max-width, gutter, hero proportions,
   section spacing.
6. **Depth & Elevation** — number of levels, exact shadow definitions.
7. **Do's and Don'ts** — three concrete each.
8. **Responsive Behavior** — desktop / tablet / phone breakpoints.
9. **Agent Prompt Guide** — three lines telling future agents how to
   keep this DS coherent.

Then proceed to Step 3 (section planning) using the new DS.

## 📚 Reference files

- **`references/board.md`** — the design board. Format classes,
  specimens, decompositions, disambiguator tables. **The primary
  routing source. Read it first.**
- **`references/directions.md`** — 5 deterministic visual directions
  with OKLch palettes + font stacks + posture cues. Used as the
  fallback in Branch A when no specimen fits the brief, and as the
  starting palette when drafting a one-shot custom DESIGN.md.
- **`references/craft.md`** — full typography / color / motion / state
  / accessibility rules with rationale and edge cases.
- **`references/laws-of-ux.md`** — full UX-laws inventory with primary
  sources and folklore corrections.
- **`references/critique.md`** — full 5-dim review workflow with
  radar chart, scoring discipline, and Keep/Fix/Quick-wins format.

## 🧭 Hard rules summary (the contract)

- ✅ **Turn 1 on a fresh brief = brief-lock form**, then stop. No
  thinking, no tool use, no work before the form.
- ✅ Classify the brief by **format class first**, specimen second.
- ✅ Read `references/board.md` before writing CSS — every time.
  Re-read the chosen specimen's decomposition pre-flight, even if
  you "remember" it.
- ✅ State the routing rationale in one sentence before proceeding.
- ✅ ALL CAPS gets `≥0.06em` letter-spacing. Display 32px+ gets
  negative tracking. Subheadings H2/H3 (20–31px) get `0 to -0.01em`
  and Emphasize weight (510–550).
- ✅ Three weights max (Read / Emphasize / Announce).
- ✅ Plan the four palette layers (neutrals 70–90% / accent 5–10% /
  semantic 0–5% / effect <1%) *before* writing CSS.
- ✅ Five required UI states for any data-bearing surface.
- ✅ `prefers-reduced-motion` honored on every transform animation.
- ✅ Self-critique on 5 dims before emitting. If 2+ dims score <6,
  rework before showing the user.
- ✅ Run the two-tier reflex check: first-order (category → palette),
  second-order (category + anti-refs → aesthetic family). Both must
  be non-obvious before emitting.
- ✅ When extracting brand from a reference, **grep the actual CSS**.
  Never guess hex from memory.
- ❌ No indigo accent, no two-stop trust gradients, no emoji feature
  icons, no invented metrics, no lorem ipsum.
- ❌ No pure `#000` / `#FFF`. No `text-align: justify` on body.
- ❌ No external CSS/JS unless the chosen specimen explicitly allows.
- ❌ No paraphrasing the artifact in chat after emitting.
- ❌ No skipping the format-classification step. If ambiguous, ASK.
- ❌ No skipping the brief-lock form on a fresh brief, even if the
  brief looks "complete enough".

## Attribution

Synthesized from the [nexu-io/open-design](https://github.com/nexu-io/open-design)
taste catalog (craft rules synced May 2026), MIT-licensed
[refero_skill](https://github.com/referodesign/refero_skill),
[Leonxlnx/taste-skill](https://github.com/Leonxlnx/taste-skill), the
Awwwards SOTD lineage, the Sequoia/YC pitch-deck canon, and
specimens contributed by the user via reference screenshots. Primary
research grounding: WCAG 2.2, Material 3 motion tokens, Bringhurst
(*Elements of Typographic Style* §3.2.7 for ALL CAPS tracking floor),
Tversky/Morrison/Bétrancourt 2002 (motion), the Yablonski Laws of UX
catalog, and Baymard Institute checkout research.
