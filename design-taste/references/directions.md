# 🧭 Direction Library

A deterministic fallback for cases where the board's specimens don't fit
the brief but the user has picked "direction for me". Each direction
ships a complete spec — palette in OKLch, font stacks, posture cues —
that you bind **verbatim** into the artifact's `:root`. No model freestyle.

> **When to reach for this file:** Branch A in SKILL.md Step 2, *after*
> you've checked the board and no specimen quite fits. The board's
> specimens are richer (component primitives, banned-pattern lists,
> photographic conventions); directions are leaner (palette + fonts +
> 4–5 posture cues). Prefer a specimen when one fits; use a direction
> when nothing does.

The five directions are designed to be **visually orthogonal** — pick
the one whose mood + references match the brief and the audience. If
two feel equally good, the user's "visual tone" answer from the
brief-lock form breaks the tie.

---

## 1. Editorial — Monocle / FT magazine

**id:** `editorial-monocle`

**Mood.** Print-magazine feel. Generous whitespace, large serif
headlines, restrained palette of off-white paper + ink + a single warm
accent. Confident, quietly intelligent.

**References.** Monocle, The Financial Times Weekend, NYT Magazine,
It's Nice That.

**Palette — drop into `:root`:**

```css
:root {
  --bg:      oklch(97% 0.012 80);     /* off-white paper */
  --surface: oklch(99% 0.005 80);
  --fg:      oklch(20% 0.02 60);      /* ink */
  --muted:   oklch(48% 0.015 60);
  --border:  oklch(89% 0.012 80);
  --accent:  oklch(58% 0.16 35);      /* warm rust / clay */

  --font-display: 'Iowan Old Style', 'Charter', Georgia, serif;
  --font-body:    -apple-system, BlinkMacSystemFont, 'Segoe UI', system-ui, sans-serif;
}
```

**Posture cues:**
- Serif display, sans body, mono for metadata only
- No shadows, no rounded cards — borders + whitespace do the work
- One decisive image, cropped only at the bottom
- Kicker / eyebrow in mono uppercase, one accent color, used at most twice
- Page numbers + section markers in mono — adds editorial chrome cheaply

**Pick when.** Long-form essay, op-ed, magazine spread, founder letter,
quarterly report, "make it feel printed".

---

## 2. Modern minimal — Linear / Vercel

**id:** `modern-minimal`

**Mood.** Quiet, precise, software-native. System fonts, near-greyscale
palette, a single saturated accent. The chrome disappears so content is
the only thing that registers.

**References.** Linear, Vercel, Notion 2024, Stripe docs.

**Palette — drop into `:root`:**

```css
:root {
  --bg:      oklch(99% 0.002 240);
  --surface: oklch(100% 0 0);
  --fg:      oklch(18% 0.012 250);
  --muted:   oklch(54% 0.012 250);
  --border:  oklch(92% 0.005 250);
  --accent:  oklch(58% 0.18 255);     /* cobalt */

  --font-display: -apple-system, BlinkMacSystemFont, 'SF Pro Display', system-ui, sans-serif;
  --font-body:    -apple-system, BlinkMacSystemFont, 'SF Pro Text', system-ui, sans-serif;
}
```

**Posture cues:**
- Tight letter-spacing on display sizes (-0.02em)
- Hairline borders only, no shadows except dropdowns / modals
- Mono numerics with `font-variant-numeric: tabular-nums`
- Sticky frosted nav, content-led layouts (no hero illustrations)
- One accent: links + primary CTA, nothing else

**Pick when.** B2B SaaS landing, dev-tool docs, AI-infra marketing,
"premium-tech-tool" vibe, anything that pairs naturally with `linear-app-saas`
on the board but where the user wants a generic direction instead of a
brand-flavored specimen.

---

## 3. Warm & soft — Stripe pre-2020 / Headspace

**id:** `warm-soft`

**Mood.** Cream backgrounds, soft accent, gentle radii. Reads like a
thoughtful product magazine — friendly without being cute. Good for
fintech, wellness, indie SaaS.

**References.** Stripe pre-2020, Headspace, Substack, Mercury.

**Palette — drop into `:root`:**

```css
:root {
  --bg:      oklch(97% 0.018 70);     /* warm cream */
  --surface: oklch(99% 0.008 70);
  --fg:      oklch(22% 0.02 50);
  --muted:   oklch(50% 0.018 50);
  --border:  oklch(90% 0.014 70);
  --accent:  oklch(64% 0.13 28);      /* terracotta */

  --font-display: 'Tiempos Headline', 'Newsreader', 'Iowan Old Style', Georgia, serif;
  --font-body:    'Söhne', -apple-system, BlinkMacSystemFont, system-ui, sans-serif;
}
```

**Posture cues:**
- Serif display, soft sans body
- Gentle radii (12–16px), no hard 0px corners on content cards
- Single accent used for primary CTA + one editorial flourish (quote mark, stat)
- Soft inner glow on hero cards rather than drop shadows
- Avoid icons; use real screenshots / photographs / illustrations

**Pick when.** Fintech marketing, wellness app, indie SaaS, "thoughtful
brand", anything where `higgsfield-friendly-editorial` is too sticker-
heavy and `linear-app-saas` is too cold.

---

## 4. Tech / utility — Datadog / GitHub

**id:** `tech-utility`

**Mood.** Data-dense, monospace-friendly, dark or light + grid. Made for
engineers and operators who want information per square inch, not vibes.

**References.** Datadog, GitHub, Cloudflare dashboard, Sentry.

**Palette — drop into `:root`:**

```css
:root {
  --bg:      oklch(98% 0.005 250);
  --surface: oklch(100% 0 0);
  --fg:      oklch(22% 0.02 240);
  --muted:   oklch(50% 0.018 240);
  --border:  oklch(90% 0.008 240);
  --accent:  oklch(58% 0.16 145);     /* signal green */

  --font-display: -apple-system, BlinkMacSystemFont, 'Inter', 'Segoe UI', system-ui, sans-serif;
  --font-body:    -apple-system, BlinkMacSystemFont, 'Inter', 'Segoe UI', system-ui, sans-serif;
  --font-mono:    'JetBrains Mono', 'IBM Plex Mono', ui-monospace, Menlo, monospace;
}
```

**Posture cues:**
- Sans display + sans body (one family) is OK here — utility trumps editorial
- Tabular numerics everywhere, mono for code / IDs / hashes
- Dense tables with hairline borders, no row striping
- Inline status pills (success / warn / danger) with restrained tinted backgrounds
- Avoid: hero images, oversized headlines, marketing copy — show the product instead

**Pick when.** Dev-tool dashboard, observability surface, incident
console, status page, anything where information density is the point
and `linear-app-saas`'s marketing-page conventions don't apply.

---

## 5. Brutalist / experimental — Are.na / Yale

**id:** `brutalist-experimental`

**Mood.** Loud type. Visible grid. System sans + a single oversized
serif. Deliberate ugliness as confidence. Great for art, indie,
agency, manifesto pages.

**References.** Are.na, Yale Center for British Art, mschf, Read.cv.

**Palette — drop into `:root`:**

```css
:root {
  --bg:      oklch(96% 0.004 100);    /* off-white printer paper */
  --surface: oklch(100% 0 0);
  --fg:      oklch(15% 0.02 100);
  --muted:   oklch(40% 0.02 100);
  --border:  oklch(15% 0.02 100);     /* borders are full-strength fg */
  --accent:  oklch(60% 0.22 25);      /* hot red */

  --font-display: 'Times New Roman', 'Iowan Old Style', Georgia, serif;
  --font-body:    ui-monospace, 'IBM Plex Mono', 'JetBrains Mono', Menlo, monospace;
}
```

**Posture cues:**
- Display = serif at extreme sizes (`clamp(80px, 12vw, 200px)`)
- Body = monospace — yes, monospace as body, deliberately
- Borders are full-strength fg (1.5–2px), not muted greys
- Asymmetric layouts: one column 70%, the other 30%
- Almost no border-radius (0–2px). No shadows. No gradients.
- Underline links, no hover decoration — let the typography carry it

**Pick when.** Manifesto, agency landing, art-school portfolio,
conference page, "make it loud", anything that pairs with the
`storage-notes-brutalist` carrousel specimen on the board but as a
landing-page / poster instead.

---

## Binding rules

When you pick a direction:

1. **Replace `:root` verbatim.** Don't improvise palette values. If
   the user wants a custom accent override, change `--accent` only —
   leave the rest of the palette as-shipped.
2. **Honor the posture cues.** They describe how the direction
   *behaves* (border weight, radius, accent budget). Composition
   decisions follow from the posture, not from your defaults.
3. **One direction per artifact.** Don't blend. If you find yourself
   wanting "modern-minimal palette with brutalist type", you have a
   custom specimen — draft it inline as a one-shot DESIGN.md (see
   SKILL.md § "Custom specimen / new format class").

## Adding a new direction

The five above are intentionally orthogonal — adding a sixth that
sits between two existing ones defeats the purpose (turns deterministic
into freestyle). Before adding, check whether the brief is better
served by:

- A new **specimen** in `board.md` (richer, component-aware) — the usual
  answer.
- A one-shot custom DESIGN.md (single-use, doesn't ship in the skill).

A new direction earns its slot only when it represents a *visual
posture* the existing five don't cover — e.g. a "dark-mode-first
brutalist" or "high-contrast accessibility-first" or "kinetic-immersive"
direction. Three or four real briefs in the new posture before
promoting.

## Attribution

The five directions and their palette/font specs are adapted from the
[nexu-io/open-design](https://github.com/nexu-io/open-design) direction
library (MIT) at `apps/daemon/src/prompts/directions.ts`. OKLch values,
font stacks, and posture cues preserved; descriptions tightened for
this skill's voice.
