# Craft rules — full reference

Universal rules that apply on top of any archetype. Brand-agnostic.
Distilled from `nexu-io/open-design/craft/` (itself adapted from
MIT-licensed refero_skill).

---

## Typography

The single most-skipped rule in AI-generated design is letter-spacing.
**No exceptions.**

### Type scale

Multiplicative scale (1.2 or 1.25). Cap at **6–8 sizes per artifact.**

| Role | Range |
|---|---|
| Display | 48–72 px |
| H1 | 32–48 px |
| H2 | 24–32 px |
| H3 | 20–24 px |
| Body | 15–18 px |
| Small | 13–14 px |
| Caption | 11–12 px |

### Line height (leading)

| Text size | Line height |
|---|---|
| Display / H1 (≥32 px) | `1.0`–`1.2` (tight) |
| Body (15–18 px) | `1.5`–`1.6` |
| Small (≤14 px) | `1.5` |

### Letter-spacing — the rule that makes or breaks craft

| Context | Letter-spacing |
|---|---|
| Body text (14–18 px) | `0` |
| Small text (11–13 px) | `+0.01em` to `+0.02em` |
| UI labels and button text | `+0.02em` |
| **ALL CAPS** | **`+0.06em` to `+0.1em` — required** |
| Subheadings H2/H3 (20–31 px) | `0` to `-0.01em` — use Emphasize weight (510–550) |
| Headings H1 (32–47 px) | `-0.01em` to `-0.02em` |
| Display (48 px+) | `-0.02em` to `-0.03em` |

The `0.06em` floor is empirical — Bringhurst's *Elements of
Typographic Style* §3.2.7 recommends 5–10% of the em for caps; modern
screen practice rounds the lower end to `0.06em`. Tighter and the
counters collide; looser than `0.1em` and the word disintegrates into
letters.

ALL CAPS without positive tracking looks cramped and amateur. Display
text without negative tracking looks loose and weak. These two
failures are the most reliable AI-slop tells.

### Font pairing

- **Maximum 2 typefaces** per artifact (display + body, or one variable
  face used at multiple weights).
- Always declare a system fallback chain. If a webfont URL is used, the
  fallback must still produce a coherent look.
- Never set `font-family: system-ui` alone on a heading — that is the
  textbook AI default. Always pair with an intentional first choice.

### Line length

Body copy at **50–75 characters per line.** CSS: `max-width: 65ch` is
a safe default.

### Three-weight system

Most well-crafted UIs use exactly three weights:

- **Read** (400/450) — body copy.
- **Emphasize** (510/550) — UI text, labels, navigation.
- **Announce** (590/600) — headlines, buttons.

Weight 700+ is rarely needed. If a design uses bold for "emphasis on
emphasis", it likely lacks weight discipline elsewhere. Soft Premium
archetype is the deliberate exception.

### Common mistakes

- ALL CAPS without `letter-spacing ≥ 0.06em`.
- Display text (≥32 px) without negative tracking.
- More than 3 type sizes visible above the fold.
- Mixed serif and slab on the same screen without a clear role split.
- Body copy in `text-align: justify` (creates rivers; never on web).

---

## Color

### Palette structure (plan all four layers before writing CSS)

| Layer | Share of pixels | Tokens |
|---|---|---|
| **Neutrals** | 70–90% | `--bg`, `--surface`, `--fg`, `--muted`, `--border` |
| **Accent** (one) | 5–10% | `--accent` only — never invent a second |
| **Semantic** | 0–5% | `--success`, `--warn`, `--danger` |
| **Effect** | <1% | gradients, glows; rarely justified |

### Accent discipline

- **At most 2 visible uses of `--accent` per screen.** Typical pair:
  one eyebrow/chip + one primary CTA. Or one accent card + one tab
  pill. Pick a pair, not a flood.
- Links count as accent — demote to `--fg` underline if a CTA is on
  the same screen.
- Hover/focus rings count as accent. Ration accordingly.

### Contrast minimums (gates, not goals)

| Pair | WCAG 2.x AA |
|---|---|
| Body text (≤16 px) on background | **4.5:1** |
| Large text (>18 px or 14 px bold) | **3:1** |
| UI components against adjacent surfaces | **3:1** |
| Focus indicator vs adjacent + unfocused state | **3:1** |

Thresholds are **inclusive** — exactly `4.5:1` passes. Don't round up;
`2.999:1` fails.

When the brand color clashes (low-contrast indigo on light is common),
darken the accent to a `600`-level shade for text use; reserve the
brand-bright variant for fills only.

### Dark themes

Avoid pure black and pure white — both cause vibration and eye strain.

| Token | Dark theme | Light theme |
|---|---|---|
| Background | `#0F0F0F` (not `#000`) | `#FAFAFA` (not `#FFF`) |
| Foreground | `#F0F0F0` (not `#FFF`) | `#111111` (not `#000`) |

On dark surfaces, prefer **semi-transparent white borders** over solid
dark borders — `1px rgba(255,255,255,0.08)` reads as structure without
adding visual noise.

### Semantic naming

Always name tokens by **purpose**, never by hue:

```css
/* good */
--accent: #2F6FEB;
--success: #17A34A;

/* bad — locks you out of theming */
--blue-500: #2F6FEB;
--green-500: #17A34A;
```

### Anti-defaults

- **Indigo `#6366f1`** (Tailwind `indigo-500`) is the most reliable
  AI-slop tell. Plus the family: `#4f46e5`, `#4338ca`, `#3730a3`,
  `#8b5cf6`, `#7c3aed`, `#a855f7`. Use the briefed `--accent`. If the
  brief truly needs indigo, make the user say so explicitly.
- **Two-stop "trust" gradient** (purple→blue, blue→cyan, etc.) on a
  hero. A flat surface + one type-driven hierarchy beats it every time.
- **Decorative gradients with no functional purpose.** Gradients
  should separate hierarchies (header → body, primary CTA → secondary),
  not decorate empty space.

### P1 soft tells (should fix)

Not P0 regressions, but signals a reviewer will catch. Fix before
shipping when the brief allows it.

- **Standard "Hero → Features → Pricing → FAQ → CTA" skeleton with no
  variation.** Introduce at least one unconventional section —
  testimonial wall as full-bleed quote, pricing as comparison-against-
  status-quo, an inline mini-product-demo.
- **External placeholder image CDNs** (`unsplash.com`, `placehold.co`,
  `picsum.photos`, `placekitten.com`). Fragile and obvious. Use an
  inline SVG placeholder or a labelled `[image: description]` block.
- **More than ~12 raw hex values outside `:root`** — tokens were not
  honoured. Move to CSS custom properties.
- **`var(--accent)` visible more than twice per screen.** Cap at 2
  visible uses. Links count as accent. Hover/focus rings count as
  accent.

### P2 polish tells (nice to fix)

- **Decorative blob or wave SVG backgrounds** — meaningless geometry.
  Use intentional shapes tied to brand language, or nothing.
- **Perfect symmetric layout with no visual tension.** Alternating
  density — one tight section, one breathing section — reads as
  intentional. Uniform spacing reads as laziness.

---

## Motion

### When motion earns its place

Tversky/Morrison/Bétrancourt's 2002 meta-analysis (IJHCS 57, pp.
247-262) found that every study claiming animation aids comprehension
had a broken control. When equalised, animation does **not** beat
static for teaching complex systems. The single use case the paper
endorses is real-time spatial or temporal reorientation: page
transitions, container morphs, viewpoint changes, progress indicators.

**Animate when** the user is moving through space, time, or state —
navigation, container expansion, progress feedback, gesture
follow-through. **Don't animate** to teach, decorate, signal "premium",
or fill silence.

### Duration thresholds

The cross-DS convergence is **150ms** — Material 3 `short3`, IBM
Carbon `moderate-01`, Shopify Polaris `150`, Tailwind default, SLDS
`duration-fast` all converge here.

| Duration | Use |
|---|---|
| 50–100 ms | Instant feedback (button press, toggle commit, hover) |
| 150 ms | Default for state-confirmation |
| 200–300 ms | Entering UI (modals, sheets, dropdowns) |
| 300–500 ms | Cross-screen transitions, container morphs |
| > 500 ms | Reserved for cross-screen, staged, or platform-native transitions |

Non-navigation microinteractions — hover, press, toggle, validation,
chip selection — should stay **under 500 ms.** Past that the user
notices motion as motion and waits on the UI.

Frequent animations (a hover effect seen 50 times per session) need to
stay **≤200 ms.** Mobile animations should run **20–30% shorter** than
desktop equivalents because travel distances are shorter.

### Curve vs spring

- **Curve** for opacity, color, and any property changing between two
  known points.
- **Spring** for position, scale, rotation, and gesture-driven motion —
  anything that should feel physical.

Material 3 standard easing is `cubic-bezier(0.2, 0, 0, 1)` —
**front-loaded**; the trailing zero makes the curve hit its target
instantly and settle. M2 standard was the symmetric `cubic-bezier(0.4,
0, 0.2, 1)`, preserved in M3 under the name `legacy`. Anyone shipping
the M2 curve and calling it "M3" is on legacy tokens.

Apple's published SwiftUI default spring is `(response: 0.5,
dampingFraction: 0.825, blendDuration: 0)`. The widely cited `.snappy
= 0.25 s, .smooth = 0.35 s` numbers are wrong — Apple's docs assign
all three presets a 0.5s base, differing only in bounce (0 / 0.15 /
0.3).

### Reduced motion

Every animation that translates, scales, rotates, or parallaxes must
respect `@media (prefers-reduced-motion: reduce)`. WebKit shipped this
in 2017 to address vestibular triggers.

Working rule: strip motion-on-an-axis (translate, scale, rotate,
parallax). Keep opacity/color crossfades as substitutes when a state
change still needs to be conveyed.

The View Transitions API does **not** apply `prefers-reduced-motion`
automatically; the author must add a query override on the
pseudo-elements or skip `startViewTransition` entirely.

WCAG 2.2.2 (Pause/Stop/Hide) is Level A — the legal floor. Vestibular
language lives in 2.3.3, which is **AAA**. WCAG 2.3.1 (Level A)
permits flashing only when there are no more than three flashes within
any one-second period. For gamified UI / celebrations / sparkles /
confetti / level-up bursts: avoid rapid flashing unless tested against
the thresholds, and prefer one-shot animations over loops.

### Repeated and ambient motion

- Cap iteration count: carousels at 3–5 cycles then pause; skeleton
  shimmer until content lands, never indefinitely.
- WCAG 2.2.2 requires a pause control for any motion running longer
  than **5 seconds**.
- Cancel ambient motion on route change.
- Reward animations are one-shot. Confetti, sparkles, level-up bursts
  fire once and dismiss; no looping timer.
- Spinners must not run indefinitely. Escalate to progress/cancel
  states and stop animation at 60s.

### Common mistakes

- "Skeleton screens feel 11% faster" — Harrison/Yeo/Hudson CHI 2010
  measured *backwards-decelerating ribbed determinate progress bars*
  (n=16). The induced-motion mechanism doesn't transfer to skeletons.
- "Doherty Threshold = 400 ms" — the 1982 paper does not contain
  "400". The lowest threshold actually measured is 300 ms.
- M2 standard easing labelled as "Material 3". M3's standard is
  `cubic-bezier(0.2, 0, 0, 1)`.
- Animations that *perform* a state change rather than *confirming*
  one that has already happened. Optimistic UI first; motion second.
- More than 500 ms on any non-cross-screen transition.
- Animation as the only signal of state change. Reduced-motion users
  miss it; always pair with a static affordance.
- Curve-based animation on a `transform: scale()` that should feel
  physical. Use a spring.

---

## Stateful UI — the five required states

The single most reliable AI-design failure is shipping only the
populated state.

| State | Triggered when | Must contain |
|---|---|---|
| **Loading** | Data is in flight | Skeleton, spinner, or shell — plus a 15s "taking longer than expected" fallback |
| **Empty** | No records yet, or query returned nothing | Headline, plain explanation, primary CTA |
| **Error** | Fetch failed, server failure, validation rejection | Plain-language cause, recovery action, preserved user input |
| **Populated** | Data present, primary case | The state the design was actually drawn for |
| **Edge** | Extreme volume, long strings, missing optional fields, RTL or long-word content, partial network | Layout that does not break |

### Edge-state test matrix (mentally run before emitting)

Concrete scenarios every artifact-class must survive. Walk through the
relevant row before emitting any data-bearing surface.

| Artifact type | Edge scenario to mentally render |
|---|---|
| Dashboard / table | 10,000+ rows; all-numeric columns; sort + filter applied; one column at 200-char title; zero rows |
| Mobile card / list | 200-char title (wraps to 4 lines); missing avatar; missing secondary CTA; one item, ten items, hundred items |
| Form | All optional fields empty; all required fields at max length; single field with validation error; submit-pending |
| Search results | Single-character query; query with only special chars (`!@#$%`); 1,000+ result count; zero results |
| Detail view | Missing all optional metadata; RTL primary content with LTR embeds (a URL inside Arabic body); deleted resource |
| Carrousel / deck | Title at 4 lines; cover with no subtitle; slide 1 of 1; slide 15 of 15 |
| Pricing table | Recommended tier highlighted; all tiers equal-content (no winner); single-tier; 4-tier with two recommended |
| Landing hero | Headline at 80 chars wrapping to 3 lines; missing tagline; missing illustration |

If you can't picture the layout surviving one of these scenarios for
the surface you're building, the layout is broken before it's
emitted.

### Loading thresholds

| Latency | Indicator |
|---|---|
| < 300 ms | None — feedback is instant |
| 300 ms – 2 s | Skeleton |
| 2 s – 10 s | Labelled spinner |
| 10 s – 60 s | Determinate bar with cancel |
| > 60 s | Stop and offer error/retry |

### Form-specific states

Forms add three on top of the five.

| State | Triggered when | Behavior |
|---|---|---|
| **Untouched** | Field has not yet had focus | Default styling; no validation messages |
| **Dirty (valid)** | User typed and field passes validation | Persistent helper text remains; no success-coloring |
| **Submitted-pending** | Submit clicked, awaiting server | Submit button enters loading state; fields lock against re-submission |

**Validation timing:** validate **on blur**, not on first keystroke.
For password and similar live fields, validate on each keystroke
*only after the first blur*. Remove the error message the instant
input becomes valid.

### Empty state composition

Empty is not the absence of state. It is its own state with a job.

- **First-use empty** — illustration + headline + value sentence +
  primary CTA. The empty is the onboarding moment.
- **No-results empty** — echo the query, suggest alternatives, never
  leave a true blank.
- **Cleared empty** — celebratory phrasing, optional next-action.
- **Error-as-empty** — never. An error is its own state with recovery
  information; do not collapse error into empty.

### Error state composition

Every error must answer three questions, in this order:

1. **What happened.** "Your card was declined." Not "Something went
   wrong."
2. **Why, if knowable.** "Insufficient funds." Or "Network unreachable
   — check your connection."
3. **What the user can do.** Retry, alternative path, or support link.

**Preserve user input across the error.** The form must not clear on
submit failure.

Severity tiers: field-level (red border + inline message) → form-level
(error summary banner + per-field markers) → section-level (inline
panel with retry, surrounding sections still functional) → page-level
(full error state with illustration and recovery CTA) → app-level
(persistent banner or modal for critical loss-of-functionality).

---

## Accessibility baseline

Target **WCAG 2.2 AA** as the working ceiling. Clears the WCAG 2.1 AA
legal floor in both EU (EAA) and US (ADA Title II 2024 final rule) and
prepares for EN 301 549 v4.1.1.

### Touch targets

| Bar | SC | Size |
|---|---|---|
| AA (legal floor) | 2.5.8 Target Size (Minimum) | **24×24 CSS px** |
| AAA (craft commitment) | 2.5.5 Target Size (Enhanced) | 44×44 CSS px |
| iOS HIG | — | 44×44 pt |
| Material 3 | — | 48×48 dp |

WCAG 2.5.8 lists five exceptions where the 24×24 minimum doesn't apply:
Spacing, Equivalent, Inline, User-agent control, Essential. The
**Spacing exception** is the one icon-buttons typically rely on — a
24-CSS-px exclusion circle around the target doesn't intersect
adjacent ones.

### Focus indicators

- Visible on every interactive element.
- 3:1 contrast against both adjacent and unfocused state.
- Don't rely on the browser default outline — style it explicitly so
  the design language extends to keyboard users.

### Color is never the only signal

Pair color contrast with a non-color signal (icon, text label,
position) for any state-conveying difference. Color blindness
affects ~8% of men. The "selected pricing tier" gets a checkmark icon
*and* the accent color, not just the accent color.

### Hit-area rule of thumb

Place high-frequency mobile controls in the natural thumb arc — bottom
half of the screen, not the top corners. Fitts's Law plus the
platform floor — never just Fitts.
