# Critique — full 5-dimension review

Run when the user explicitly asks for a "design review", "design
audit", "critique this", "what's wrong with my design", or as a
self-check before emitting any artifact.

Distilled from `nexu-io/open-design/skills/critique/SKILL.md`
(itself inspired by the *huashu-design* expert-critique flow).

---

## When to use

- After an artifact is generated and the user asks "what's wrong with
  this?" or "review this".
- As a self-check loop **before** emitting an artifact (use the short
  form — score quickly, fix the worst, re-emit).
- When comparing two variants of the same design.

## What you produce (full review mode)

A single self-contained `<artifact type="text/html">` review report
including:

1. **Header** — what artifact was reviewed, date, reviewer ("Design
   Taste · Critique"), 1-line verdict.
2. **Radar chart** (inline SVG, no library) showing the 5 scores.
3. **Five dimension cards**, each with:
   - Score 0–10 with band: 0–4 *Broken* · 5–6 *Functional* · 7–8
     *Strong* · 9–10 *Exceptional*.
   - 1-paragraph evidence (cite specific elements / classes / lines).
   - One Keep / Fix / Quick-win bullet.
4. **Combined action lists** at the bottom:
   - **Keep** (3–5 bullets) — what's working, don't touch.
   - **Fix** (3–6 bullets) — P0/P1 issues, ordered by visual cost
     saved per minute spent.
   - **Quick wins** (3–5 bullets) — 5–15 minute tweaks with
     disproportionate impact.

## What you produce (self-check mode, short form)

Internal only. No HTML report. Score each dimension in 1 sentence with
specific evidence. If two or more land below 6, **rework before
emitting**.

---

## The 5 dimensions

> Each dimension is independent — a deck can be 9/10 on Innovation but
> 4/10 on Hierarchy and the report should say so plainly. Don't
> average away interesting failures.

### 1. Philosophy consistency · 哲学一致性

> Does the artifact pick a clear *direction* and stick to it through
> every micro-decision (chrome / kicker / spacing / accent)?

**Evidence to look for:**

- Is there one declared design direction (one of the four archetypes,
  or a coherent custom DESIGN.md) — or is it three styles in a trench
  coat?
- Does the chrome / kicker vocabulary stay in one register? Or does
  page 3 say "Vol.04 · Spring" and page 7 say "BUT WAIT 🔥"?
- Are accent / serif / mono used by the same rule throughout?

**Bands:**
- **0–4** Three styles fighting each other.
- **5–6** One direction but half the elements drift.
- **7–8** Coherent, occasional drift on edge pages.
- **9–10** Every element argues for the same thesis.

### 2. Visual hierarchy · 视觉层级

> Can a stranger figure out what to read first, second, third —
> without being told?

**Evidence to look for:**

- Is the largest type clearly the most important thing on each page?
- Do mono / serif / sans roles match the information's *role* (meta /
  body / display)?
- Lots of "loud" elements competing? Or a clear primary + secondary +
  tertiary tier?

**Bands:**
- **0–4** Everything shouts.
- **5–6** Hierarchy works on hero pages but breaks on body.
- **7–8** Clear tiers, occasional collision.
- **9–10** Eye moves with zero friction.

### 3. Detail execution · 细节执行

> The 90/10 stuff — alignment, leading, kerning at large sizes, image
> framing, foot/chrome polish, edge-case spacing.

**Evidence to look for:**

- Big-stat pages: does the number sit on a baseline, or float?
- Left/right column tops aligned in any 2-column grid?
- Image + caption proportions consistent across pages/sections?
- Mono labels: same letter-spacing? same uppercase rule?
- Any orphaned `<br>` causing 1-character lines?
- ALL CAPS without `≥0.06em` tracking? Display without negative
  tracking? (These are P0 typography fails.)

**Bands:**
- **0–4** Visible tape and string.
- **5–6** Most pages clean, 1–2 ragged.
- **7–8** Polished, expert eye finds 2–3 misses.
- **9–10** Magazine-grade — the kind of detail printed-by-hand
  typographers nod at.

### 4. Functionality · 功能性

> Does the artifact *work* for its intended use? Click targets, nav,
> readability at presentation distance, copy-paste-ability for code
> blocks, mobile fallback if relevant.

**Evidence to look for:**

- Deck: keyboard / wheel / touch nav all working? Iframe scroll
  fallback?
- Landing: CTA above the fold? Phone number tappable on mobile?
- Runbook: code blocks copyable, mono font, no smart quotes?
- Critical info readable from 4m away (large screen presentation)?
- All five UI states present on data-bearing surfaces?
- Touch targets ≥`24×24 CSS px`? Focus indicators visible?
- `prefers-reduced-motion` honored on transform animations?

**Bands:**
- **0–4** Visually fine but doesn't accomplish its job.
- **5–6** Core flow works, edge cases broken.
- **7–8** Robust through normal use.
- **9–10** Defensively engineered — handles iframe / fullscreen /
  paste / print without flinching.

### 5. Innovation · 创新性

> Does this push past the median? Is there one element that makes
> people lean in?

**Evidence to look for:**

- One *unexpected* layout / motion / typographic move that wasn't
  required?
- Or 100% safe — could be any deck/landing from any agency?
- Is the innovation *earned* (matches the chosen archetype) or
  grafted on (random WebGL on a Kinfolk slow-living deck)?

**Bands:**
- **0–4** Generic AI-slop median.
- **5–6** Competent and unmemorable.
- **7–8** One memorable moment, the rest solid.
- **9–10** Multiple moves you'd steal — but each one obviously serves
  the thesis.

---

## Scoring discipline (read before you score)

- **Always cite evidence.** "Scored 4 because hero page mixes Playfair
  display with Inter sans on the same line" beats "feels inconsistent."
  Numbers without evidence get rejected.
- **Don't average up.** If Hierarchy is 5 because page 3 is broken,
  don't bump to 7 because pages 1 and 2 are fine. The score is the
  **worst sustained band.**
- **Don't grade-inflate.** A 7 means *strong*, not *acceptable*. If
  every score is 7+, you're not reviewing critically. Mean above 8
  across all 5 is suspicious.
- **Innovation is allowed to be low.** 5/10 is fine for production
  deliverables. Don't punish *appropriate* conservatism.

---

## Workflow (full review mode)

### Step 1 — Acquire the artifact

Three modes:

1. **Project file** — user said "review the index.html I just made":
   open it from the project folder.
2. **Pasted HTML** — user pasted code in the chat: read it from the
   message.
3. **Generated by you in this turn** — you just emitted an artifact
   above and want to self-critique: re-read your own `<artifact>`.

If multiple HTML files exist, ask which one (don't review all).

### Step 2 — Read enough to score

Skim the entire `<style>` block, then read 6–8 representative content
blocks. **Do not score from frontmatter alone.** The score depends on
*executed* design, not declared intent.

### Step 3 — Score with evidence

For each of the 5 dimensions, write the score and a 30–80 word
evidence paragraph that names specific elements. Use line numbers,
class names, page numbers.

Example:

```
Dimension: Detail execution
Score: 6 / 10
Evidence: Stat-cards on page 3 align cleanly (grid-6, 3×2), but on
page 8 the right column foot sits 2vh higher than the left because
.callout has 3vh top margin while the figure doesn't. Image captions
use mono on page 5 but sans on page 7 — pick one.
```

### Step 4 — Build the action lists

Aggregate the 5 evidence paragraphs into:

- **Keep** (3–5 bullets) — concrete things working that the user must
  not break in the next iteration. Cite by class / page / element.
- **Fix** (3–6 bullets) — must-do, ordered by *visual cost saved per
  minute spent*. Each bullet ≤ 1 sentence.
- **Quick wins** (3–5 bullets) — 5–15 minutes each, high
  signal-to-noise (e.g. "swap `display:flex` for `grid` on page 4 to
  fix the column drift").

### Step 5 — Emit the report HTML

Build a single file:

- Header: artifact name + reviewer credit + date.
- Big radar chart (SVG, inline).
- 5 dimension cards in a 1-column or 2-column grid.
- Three action lists at the bottom with checkbox affordance.

Use the active archetype tokens if one was chosen; otherwise default
to Neutral Default (off-white background, near-black text, one accent
for radar fill).

---

## Output contract (full review mode)

```
<artifact identifier="critique-<artifact-slug>" type="text/html"
          title="Critique · <Artifact Title>">
<!doctype html>
<html>...</html>
</artifact>
```

One sentence before the artifact ("Reviewed X across 5 dimensions, see
report below.") and **stop after `</artifact>`** — do not paraphrase
the report in chat; the user will read the artifact.

---

## Hard rules

- **5 scores, every time.** Partial reports are not allowed.
- **Evidence per score.** No "feels off" / "needs work". If you can't
  cite an element, the score is not justified.
- **Don't grade-inflate.** Overall mean above 8 is suspicious; check
  yourself.
- **Don't review your own artifact in the same turn.** The user needs
  to see it first. Self-critique only on explicit request ("now
  critique what you just made"). The exception is the silent
  self-check before emitting — that one is internal and never written
  to chat.
- **Single-file HTML only.** No external CSS/JS. Inline everything.
- **Radar chart is mandatory.** Gives the report a recognizable
  silhouette and lets the user spot weak axes at a glance.

---

## Radar chart skeleton (paste-ready)

```html
<svg viewBox="0 0 400 400" xmlns="http://www.w3.org/2000/svg" role="img"
     aria-label="Five-dimension critique radar">
  <!-- grid rings: 2, 4, 6, 8, 10 -->
  <g stroke="var(--border)" fill="none" stroke-width="1">
    <polygon points="200,40  336.6,140  284.7,300  115.3,300  63.4,140"/>
    <polygon points="200,80  308.9,160  267.6,280  132.4,280  91.1,160"/>
    <polygon points="200,120 281.2,180  250.4,260  149.6,260  118.8,180"/>
    <polygon points="200,160 253.6,200  233.2,240  166.8,240  146.4,200"/>
  </g>
  <!-- axes -->
  <g stroke="var(--muted)" stroke-width="1" opacity="0.4">
    <line x1="200" y1="200" x2="200" y2="40"/>
    <line x1="200" y1="200" x2="336.6" y2="140"/>
    <line x1="200" y1="200" x2="284.7" y2="300"/>
    <line x1="200" y1="200" x2="115.3" y2="300"/>
    <line x1="200" y1="200" x2="63.4" y2="140"/>
  </g>
  <!-- score polygon: replace with computed points based on (score/10) -->
  <polygon points="<computed>" fill="var(--accent)" fill-opacity="0.15"
           stroke="var(--accent)" stroke-width="2"/>
  <!-- labels -->
  <g font-family="var(--mono)" font-size="11"
     letter-spacing="0.06em" text-transform="uppercase"
     fill="var(--fg)" text-anchor="middle">
    <text x="200" y="28">Philosophy</text>
    <text x="350" y="138">Hierarchy</text>
    <text x="294" y="320">Detail</text>
    <text x="106" y="320">Function</text>
    <text x="50"  y="138">Innovation</text>
  </g>
</svg>
```

The five vertices, in order, sit at angles `-90°, -18°, +54°, +126°,
+198°` from center `(200, 200)`. Score `s` (0–10) maps to radius
`(s/10) * 160`. Compute the score polygon's points by:

```
x = 200 + (s/10) * 160 * cos(θ)
y = 200 + (s/10) * 160 * sin(θ)
```

Use `font-variant-numeric: tabular-nums` if rendering scores in mono.
