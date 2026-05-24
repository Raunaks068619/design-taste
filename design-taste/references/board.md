# 🗂️ Design Board v1

The living taxonomy. Each format class holds specimens. Each specimen has a decomposition + trigger logic. When a brief lands, we route brief → class → specimen → execute.

---

## 📱 Class: Instagram Carrousel
*Vertical 1080×1350, swipe nav, no fold, single brand-mark band repeating across slides.*

### `storage-notes-brutalist` 🗞️
*From Raunak — the deck Claude generated unprompted.*

- **Vibe** — Swiss industrial print as Instagram manifesto. Black ink on warm paper, hazard red as the only second color, viewport-bleeding grotesque, register strips, monospace metadata.
- **Substrate** — `#F4F4F0` newsprint, `#050505` ink, `#E61919` hazard red.
- **Display** — Heavy neo-grotesque (Archivo Black / Neue Haas Grotesk Black) at viewport-bleeding scale, tracking `-0.04em`, `line-height: 0.88`, **uppercase only**.
- **Body** — Monospace (JetBrains Mono / IBM Plex Mono), uppercase, fixed `10–13px`, `letter-spacing: 0.1em`.
- **Accent rule** — One word per slide gets the hazard red treatment. Same word-as-noun device repeats across the whole deck.
- **Components** — Top register strip (issue/date/page), numbered theses with hairlines, `display: grid; gap: 1px` on ink-bg data tables, ASCII syntax (`[ LABEL ]`, `>>>`, `///`) ≥3× per deck, closing colophon.
- **Banned** — `border-radius` >0, drop shadows, gradients, glassmorphism, sans-serif body, centered text, any color outside ink/paper/red.
- **Pick when** — manifesto, technical comparison, declarative thesis, "rigor over friendliness", agency portfolio, newspaper energy, conference notes, deep dive. **Don't pick** for tutorial, friendly explainer, brand campaign.

### `higgsfield-friendly-editorial` ✨
*From the Higgsfield "Claude Skill for AI Video Automation" carrousel.*

- **Vibe** — Course-creator carrousel. Warm peach-cream substrate, terracotta serif numerals, hand-drawn stickers + arrows, dark macOS file-tray cards with Finder-style icons, terminal pills with syntax highlighting.
- **Substrate** — `#FCEDDC` warm peach-cream (NOT pure white).
- **Display** — Transitional serif (Fraunces / Recoleta / DM Serif Display), weight 700, in `--accent-1` terracotta.
- **Body** — Inter / SF Pro at weight 500, near-black.
- **Accents (TWO)** — `--accent-1: #A8431F` terracotta for serif display, `--accent-2: #D4FC4D` chartreuse highlighter for sticker chips.
- **Components** — Numbered serif headers (`1.`, `3.`, `4.`), dark file-tray cards (`#1A1A1A` bg, warm `--tray-rim` 2–3px outer border, soft warm-tinted shadow, contains macOS Finder folder icons + filenames in white), terminal code pills (dark bg, syntax-colored: paths blue `#4A9EFF`, strings green `#6FCF97`, function names yellow `#F2C94C`), sticker layer (max 2 per slide top-right: chartreuse chip with squiggle + terracotta starburst), ONE hand-drawn arrow per slide pointing text → screenshot.
- **Cover slide convention** — Full black bg with 3D extruded brand mark + neon rim-light, deck title in chunky rounded sans below.
- **Banned** — More than 2 stickers per slide. Squiggle-as-bullet. Light tray cards. Replacing macOS-style icons with abstract glyphs.
- **Pick when** — tutorial, course explainer, friendly how-to, "Lenny's-style", "Ali Abdaal-style", course creator energy, ConvertKit/Maven vibe.

### `mobile-editing-high-fashion` 👗
*From the Mobile Editing Club "Figma & Claude for Brands" carrousel.*

- **Vibe** — Agency/luxury Instagram. Cream substrate, tight grotesque + italic serif partner, photographic covers with type overlapping the subject, Figma-mockup-as-content cards, marker-pen annotations, no color accent.
- **Substrate** — `#F0E9E1` warm sand, slightly desaturated. Foreground `#1A1410` near-black warm-tinted (never `#000`).
- **Display** — Tight grotesque (Söhne / GT America / Neue Haas Grotesk Display), weight 700–800, tracking `-0.04em`, line-height `0.92`. 80–120pt cover, 56–72pt content.
- **Italic partner** — DM Serif Display Italic / Noe Display Italic on a 2–4 word phrase that completes the headline ("for Brands", "at once"). Used **once per slide max**.
- **Body** — Same grotesque at weight 400, 14–16pt, tracking 0, line-height 1.45.
- **Hand-marker** — Caveat / Permanent Marker for annotations only. Never headlines.
- **Cover slide convention** — Full-bleed photograph (real model, real product), brand wordmark stacked top-center, headline overlapping bottom 20–30% of photo (characters slice into subject — signature move), italic partner one line below, white rounded-full pill CTA at bottom with `→`.
- **Content slide convention** — One headline, one body paragraph (≤4 lines, max-width ~38ch), one piece of visual content. Visual content is **the product** — UI mockups in realistic Figma/browser chrome, real packaging photos, real screenshots. At most ONE handwritten note + ONE marker arrow per slide. "SWIPE" pill bottom-right.
- **Banned** — Any color outside cream/ink palette (brand colors only appear *within* photographed products). 3D renders. Vector illustrations. Stock icons. Sticker layers. Emoji. Drop shadows on cards (Figma chrome IS the depth). Centered body copy.
- **Pick when** — "luxury brand", "agency portfolio", "premium course", "designer Instagram", "campaign deck", "Mobile Editing Club style", "Off-White-style", "ALD-style".

### Disambiguator: friendly vs high-fashion
Both use warm cream. Decide via these signals:

| Signal | → friendly-editorial | → high-fashion |
|---|---|---|
| Cover treatment requested | "make it fun / playful" | "make it editorial / fashion / premium" |
| Subject | tutorial, course, normal users | brand campaign, agency case study |
| Reference name dropped | Lenny / Ali Abdaal / ConvertKit | Mobile Editing / ALD / Off-White |
| 3D / illustration assets needed | yes | no — photographic only |
| Tone test | "would Lenny put a squiggle here?" | "would a fashion AD allow ornament?" |

---

## 🌐 Class: Website Landing Page
*Desktop 1440px+ baseline with responsive collapse, fold matters, hover states earn attention, CTA hierarchy is everything.*

### `linear-app-saas` ⚪
*Linear/Notion/Vercel marketing-page lineage. The 2026 SaaS default for "premium tech tool".*

- **Vibe** — Calm, dense, technical confidence. Dark or light, but always one substrate. Heavy on type hierarchy, heavy on product shots, light on illustration.
- **Substrate** — `#0A0A0A` dark or `#FAFAFA` light. Surfaces at `#111111` / `#FFFFFF`. Hairlines `rgba(255,255,255,0.08)` on dark.
- **Display** — Inter / Geist / GT America at weight 600, tracking `-0.02em` on display, max H1 64–80px.
- **Body** — Same family, weight 400, 16–18px, line-height 1.5.
- **Accent** — One brand color (`--accent`), used MAX 2× per fold (eyebrow + CTA). Links demote to underlined fg if CTA exists.
- **Section rhythm** — Hero → social proof bar → 3 features split-image → metrics strip → testimonial → pricing → CTA → footer. Don't deviate without reason.
- **Components** — Floating glass-pill nav (`backdrop-filter: blur`), big product screenshot in hero with subtle device frame, hairline-bordered feature cards (no fill), customer logo marquee (slow infinite, pause on hover), tabular pricing with one tier marked "recommended" and visually distinct, FAQ accordion, footer with mono metadata.
- **Motion** — Scroll entry: `translateY(12px) → 0` + `opacity 0 → 1`, `600ms cubic-bezier(0.16, 1, 0.3, 1)`. IntersectionObserver only. Honor `prefers-reduced-motion`.
- **Banned** — Two-stop trust gradient on hero (purple→blue, etc). Indigo `#6366f1` accent. Stock-photo-people-pointing-at-laptop. Centered hero H1 over a dark blurred image. Sliders/carousels for testimonials.
- **Pick when** — B2B SaaS, dev tool, productivity app, AI infra, "Linear-style", "premium SaaS", "developer-focused".

### `awwwards-kinetic` 🎬
*Awwwards SOTD lineage — heavy WebGL, kinetic type, scroll-driven storytelling. Studio Namma, Obys, Bruno Simon territory.*

- **Vibe** — Studio portfolio energy. Site IS the demo. Performance and motion craft are the product.
- **Substrate** — Often dark (`#0E0E0E`) but can be cream. Photo or render takes 100vh. Type-heavy interludes between visual sections.
- **Display** — Custom or distinctive variable font (Migra / Fraunction / Söhne Mono), large, often kinetic (variable-axis animated on scroll).
- **Body** — Smaller than Linear-style (14–15px), usually mono for technical content, sans for narrative.
- **Accent** — One accent, often saturated (`#E61919` red, `#F2FF49` yellow, `#3A30FF` electric blue).
- **Hero** — Full-bleed video / WebGL scene / interactive 3D, autoplay muted, with delayed text overlay (1–2s after load).
- **Components** — Full-bleed videos between sections, scroll-pinned sequences (image stays, text changes), kinetic type that transforms on scroll, custom cursor, project case studies as immersive scrollytelling chapters.
- **Motion** — Heavy. Scroll-linked transforms. GSAP/ScrollTrigger or Framer-Motion equivalent. Cubic-bezier easings, never linear.
- **Banned** — Stock UI screenshots. Tabular pricing (this isn't that kind of site). Plain logo wall.
- **Pick when** — agency portfolio, studio site, conference site, art project, brand launch, "Awwwards-tier", "kinetic", "WebGL".
- **⚠️ Warning** — High execution cost. Don't pick if the brief is a startup MVP.

### `apple-product-launch` 🍎
*Apple/Linear/Arc product-page lineage. Premium consumer SaaS or hardware launch.*

- **Vibe** — Cinematic product reveal. Long page, scroll = chapter transitions. Each section = one feature, big hero shot, calm copy.
- **Substrate** — Alternates: black sections + white sections + tinted section per feature. Each feature gets its own color world (sampled from product photo).
- **Display** — Heavy weight (700+) Geist / SF Pro Display / Cabinet Grotesk, `clamp(48px, 7vw, 96px)`, line-height `0.96`, tracking `-0.035em`.
- **Body** — Same family weight 400, max-width 52ch, line-height 1.5.
- **Accent** — None as a token — accent comes from product photo dominant color.
- **Components** — Floating-pill nav (Soft Premium archetype). Asymmetric hero with massive display + small lede. Double-bezel cards. Button-in-button CTA pills with circular `→` wrapper. Z-axis cascade or split image module per feature. Customer logo marquee. Inverted dark closing band.
- **Motion** — Springy. `cubic-bezier(0.32, 0.72, 0, 1)` minimum 700ms. Scroll-entry blur from 8px → 0.
- **Pick when** — premium consumer product launch, hardware site, "Apple-like", "Linear-tier", "$150k agency feel", consumer SaaS where calm and weight matter.

### Disambiguator
| Signal | linear-app | awwwards-kinetic | apple-launch |
|---|---|---|---|
| Subject | B2B tool | studio/portfolio/art | consumer product |
| Performance budget | tight (LCP <2s) | loose (motion is the product) | tight |
| Visual content | screenshots | full-bleed video/WebGL | hero-shot photography |
| Goal | sign-up conversion | inquiry / portfolio review | brand impression + sign-up |

---

## 🎛️ Class: SaaS Dashboard / Admin Panel
*Application UI, dense data, sustained-use surface. Different rules from marketing pages — clarity > impression.*

### `linear-issue-tracker` 🟣
*Linear / Height / Cron lineage. The 2026 default for "tasteful product UI."*

- **Vibe** — Keyboard-first, dense but breathing, no chart-junk. Operational, not analytical.
- **Substrate** — Dark `#0A0A0A` with `#0F0F0F` surfaces, OR light `#FAFAFA` with `#FFFFFF` surfaces. Pick one per app.
- **Display** — Inter at weight 500–600, 13–14px UI text, no display-size headings inside the app.
- **Body** — Inter 400, 13–14px.
- **Accent** — Single brand color used at <5% of pixel area. Used for: focused row, primary CTA, status pill, notification dot. Never for borders, never for backgrounds.
- **Layout** — Three-pane: left sidebar (collapsible, 240–280px) + main content + optional inspector right pane (320–400px). Content area uses 12-col grid only when a marketing surface is embedded; otherwise free flow.
- **Components** — Command palette (⌘K) is mandatory. Status pills (radius `999px`, 11px uppercase mono with `letter-spacing: 0.06em`). Hairline-bordered list rows with hover background `rgba(0,0,0,0.04)`. No card chrome on data rows. Sortable table headers. Keyboard-shortcut hints inline (e.g. `Press ⌘K to search`).
- **Charts** — Sparklines inline in tables. Line charts for trends. Bar charts for comparisons. **No pie charts**, no donut charts unless ≤3 segments and the part-to-whole is the actual question.
- **Empty states** — First-use empty: illustration + headline + value sentence + primary CTA. No-results: echo the query. Cleared: celebratory.
- **Banned** — Glassmorphism. Decorative gradients. Pie charts >3 segments. Random colors per metric. Red for anything that isn't broken (traffic-light discipline). Skeumorphic icons. Tabular nums turned off in number columns.
- **Pick when** — issue tracker, project management, dev tool dashboard, internal admin, "Linear-style", "Height-style", anything where keyboard speed > visual flair.

### `vercel-developer-console` 📊
*Vercel / Supabase / Stripe Dashboard lineage. Developer-facing analytics with deployment/infra metaphor.*

- **Vibe** — Real-time deploys, terminal-adjacent. Mono everywhere. Code is content, not aside.
- **Substrate** — Almost always dark `#0A0A0A`. Surface `#0F0F0F`. Hairlines `rgba(255,255,255,0.08)`.
- **Display** — Inter / Geist 600 for cards, Geist Mono 500 for IDs/timestamps/code.
- **Accent** — One brand accent for primary action. Plus semantic: green `#17A34A` for success/healthy, amber `#F2C94C` for warning, red `#DC2626` for failure. Status colors are non-negotiable, not stylistic.
- **Components** — Real-time log stream (mono, syntax-highlighted, autoscroll with pause-on-hover). Deployment timeline (vertical strip with status dots, clickable). Resource graphs (line charts with tabular-nums labels). Breadcrumb nav with project/branch/env selector. CLI-equivalent shown next to UI action ("or run `vercel deploy`"). Copy-to-clipboard everywhere.
- **Charts** — Line charts dominant. Heatmaps for traffic patterns. Real-time tickers. Always `font-variant-numeric: tabular-nums` on numeric columns.
- **Banned** — Light mode without explicit toggle. Cute illustrations in empty states. Icons without text labels (developer audience reads).
- **Pick when** — developer tool, infra console, deployment platform, observability, anything where the user is already in their terminal.

### `notion-stripe-analytics` 📈
*Stripe Dashboard / Notion analytics / customer-facing analytics product. Operational AND analytical.*

- **Vibe** — Polished, mixed, customer-facing. Charts as first-class content. Big number → small chart → table drill-down.
- **Substrate** — Light `#FAFAFA` default with optional dark mode. Surfaces white. Brand accent more visible than Linear-style (still ≤10% pixel area but can do colored chart fills, not just dots).
- **Display** — Brand sans (often Inter/Söhne), 24–32px section headers, 36–48px for North-Star Metric in top-left quadrant.
- **Components** — Top-left quadrant ALWAYS holds the North-Star Metric (largest number, sparkline, period delta). Operational dashboards: action widgets (next-best-action lists). Analytical dashboards: filter chips persistent at top, breadcrumb-with-applied-filters. Pivot table support. Export-to-CSV always available.
- **Charts** — Line for trends, bar for compare, sparklines inline, heatmap for time-of-day patterns. Use color sparingly — one brand color + neutrals.
- **Banned** — Pie charts of >3 segments. Charts where you have to hover to read the basic gist. Dashboards >12 widgets above the fold (split into tabs). "Data vomit" maximalism.
- **Pick when** — analytics product, financial dashboard, customer-facing reporting, B2C "your stats" page (Spotify Wrapped energy applied to product).

### Disambiguator
| Signal | linear-issue-tracker | vercel-console | notion-stripe |
|---|---|---|---|
| Primary user task | manage items | monitor systems | understand trends |
| Density | high (lists/tables) | medium-high (logs+graphs) | medium (KPI cards) |
| Default theme | either | dark | light + dark toggle |
| Audience | knowledge worker | developer | analyst / business user |

---

## 🧱 Class: Component / UI Mockup
*Single-component or single-screen showcase. Used for design-system pages, component-library docs, portfolio shots, dribbble-style hero shots.*

### `shadcn-radix-baseline` 🧩
*shadcn/ui + Radix primitives lineage. The 2026 default for tasteful component design.*

- **Vibe** — Minimal, functional, themeable. The component is the content.
- **Tokens** — `--radius: 8px`, `--border: 1px solid hsl(0 0% 90%)` light or `hsl(0 0% 15%)` dark, `--ring: 2px solid hsl(var(--accent) / 0.4)` for focus.
- **Type** — Inter only. 14px UI default.
- **States** — Always show: default, hover, focus, active, disabled, loading, error, empty (where applicable). 7-state matrix is the deliverable, not just the populated state.
- **Density** — Compact (32px row height) and comfortable (40px) variants for tables/lists.
- **Banned** — Custom radii outside `0 / 4 / 8 / 12 / 9999px`. Drop shadows above `0 1px 2px rgba(0,0,0,0.04)`. Color outside foreground/background/border/accent + semantic (success/warn/danger).
- **Pick when** — design-system docs, component library showcase, default-tasteful-UI, "shadcn-style", utility-first React component.

### `arc-browser-playful` 🎯
*Arc Browser / Linear's onboarding / Cron's launch screen. Component design with personality.*

- **Vibe** — Functional but warm. Hand-tuned animations. Not strictly minimal — willing to use color, illustration, or motion to delight.
- **Tokens** — Same as shadcn but with one extra `--decorative` color (gradient OK here, capped to one per surface). Larger radii allowed (`16–24px` on cards).
- **Components** — Hero illustration in empty states. Greeting copy that uses time-of-day awareness ("Good morning, Raunak"). Easter eggs in microcopy.
- **Motion** — Spring physics on entrance. `transform: scale(1.02)` on hover. Subtle bounce on tap (`transform: scale(0.98)` then back).
- **Pick when** — consumer app, onboarding screen, hero component for marketing, anywhere personality > pure utility.

### `figma-canvas-mockup` 🎨
*The "show component as if it lives inside a design tool" pattern from Mobile Editing Club et al.*

- **Vibe** — Component embedded in mock Figma/browser chrome — the chrome is the depth.
- **Components** — Real Figma top-bar (file name, share button, zoom %, presence avatars), component centered in canvas at 44–60% scale, optional comment-thread thread bubble.
- **Pick when** — showcasing a Figma plugin, design-tool integration, "look-at-this-shipping" component shot.

### Disambiguator
| Signal | shadcn-baseline | arc-playful | figma-canvas |
|---|---|---|---|
| Audience | other devs/designers | end users | marketers/buyers |
| Goal | demonstrate API | demonstrate delight | demonstrate context |
| Motion budget | minimal | medium | none |

---

## 🪧 Class: Poster / Print
*Single-image artifact, no scroll, no interaction. Composition is everything.*

### `swiss-international` 📐
*Müller-Brockmann / Hofmann / Ruder lineage. The grandfather of modern poster design.*

- **Vibe** — Mathematical grid, sans-serif, asymmetric balance. Photography or geometric forms. Maximum clarity.
- **Substrate** — White or off-white. Foreground black. Sometimes single accent (red, yellow, blue).
- **Type** — Helvetica / Akzidenz-Grotesk / Univers. Sans-serif only. Tight tracking on display, ranged-left composition.
- **Grid** — Visible 6 or 12-column with hard-left baseline. Type aligned to the grid, no exceptions.
- **Components** — Massive sans-serif headline, dense block of body text in narrow column, single hero image (photo or geometric form), small mono metadata at edges.
- **Banned** — Decoration. Multiple accents. Centered composition (almost always). Drop shadows. Gradients.
- **Pick when** — concert poster, lecture poster, exhibition poster, "Swiss design", "Müller-Brockmann-style", anywhere clarity-as-luxury matters.

### `bauhaus-geometric` 🔴
*Bayer / Moholy-Nagy / Tschichold lineage. Form follows function but with geometric soul.*

- **Vibe** — Primary colors (red `#E61919`, yellow `#F2C94C`, blue `#3A30FF`), pure geometric forms (circle, square, triangle), heavy geometric sans.
- **Substrate** — Cream `#F4F4F0` or off-white.
- **Type** — Futura / Kabel / Gill Sans (or contemporary clones). Often display-only with all-lowercase headlines.
- **Components** — Geometric form composition (circles overlapping squares, diagonal divisions), color blocks meeting at hard edges, one bold headline, minimal supporting type.
- **Banned** — Photography. More than 4 colors total. Curves outside circles. Gradients (this is pre-gradient).
- **Pick when** — design-school energy, art school poster, modern brand harkening to modernism, "Bauhaus-style", "geometric".

### `japanese-minimal` 🌙
*Kenya Hara / Ikko Tanaka / Helmut Schmid (Tokyo era) lineage. Negative space as content.*

- **Vibe** — `Ma` (negative space) is the design. One small object on a vast field. Subtle, contemplative.
- **Substrate** — Always off-white `#F8F6F0`-ish, or warm gray. Never pure white.
- **Type** — Mixed Latin sans (very small, often 9–12pt) with Japanese characters at display scale, OR all-Latin in a Garamond/Caslon serif at small body size.
- **Composition** — 70%+ of the canvas is empty. A single object (photo, illustration, or character) anchored off-center, rule of thirds.
- **Banned** — Filling the canvas. Multiple competing focal points. Loud color. Decoration of any kind.
- **Pick when** — luxury brand poster, gallery exhibition, "Muji-energy", contemplative subject.

### `maximalist-anti-design` 💥
*David Carson / The Designers Republic / contemporary "anti-design" lineage.*

- **Vibe** — Rules broken with intent. Type on top of type. Layered, illegible-at-first-glance, rewards close reading.
- **Substrate** — Often photographic or layered textures. No safe area.
- **Type** — Mixed everything. Trash type meets refined serif. Type-as-image. Stretched, distressed, layered.
- **Components** — Overlapping type, transparency play, rule violations (text running off-edge, words split across columns), grunge textures, pasted-photocopy aesthetic.
- **Banned** — Rules. (Truly — but each violation must be deliberate and contribute to the message.)
- **Pick when** — music poster, club night, zine cover, fashion editorial, "Carson-style", "anti-design", subcultural.
- **⚠️ Warning** — Easy to do badly. Picks itself only when the subject genuinely is countercultural — applied to a SaaS ad it just looks broken.

### Disambiguator
| Signal | swiss-international | bauhaus-geometric | japanese-minimal | maximalist |
|---|---|---|---|---|
| Color count | 1–2 | 3–4 (primaries) | 1 (just ink) | many |
| Composition density | medium | medium-high | very low | very high |
| Subject | conference, lecture, exhibition | brand, school | luxury, gallery, contemplative | music, fashion, subculture |

---

## 📊 Class: Pitch Deck / Slides
*16:9 desktop or 9:16 vertical, 8–15 slides typical, presented live or shared as PDF.*

### `sequoia-classic` 💼
*Sequoia 10-slide template / YC seed deck / a16z standard. The investor default.*

- **Vibe** — Disciplined, restrained, story-first. Investor pattern-matches in 30 seconds.
- **Slide structure** — Problem → Solution → Why Now → Market Size → Product → Traction → Business Model → Team → Ask. 10 slides max. Don't deviate.
- **Substrate** — Dark navy `#0E1729` OR pure white. Pick one and stay. Dark dominates in 2026 demo days.
- **Display** — Inter / Söhne / Geist 700 for headlines (28–40pt), 600 for slide titles (20–24pt).
- **Body** — Same family weight 400, 16–18pt, max 4 bullets per slide.
- **Charts** — Line for traction, bar for market sizing, table for unit economics. Numbers are LARGE and tabular-nums. One chart per slide max.
- **Components** — Slide number bottom-right. Company logo bottom-left. Title at top with hairline divider. One big idea per slide. Speaker-notes panel filled (this gets emailed).
- **Banned** — More than 10 slides for seed/Series-A. Animation transitions between slides (looks amateur on stage). Stock photos of diverse-people-laughing-at-laptop. Generic icons. Logos of investors not actually committed.
- **Pick when** — fundraising deck (seed/A/B), "Sequoia-style", "YC-style", any context where a partner skim-reads in 90 seconds.

### `pitch-com-modern` ✨
*Pitch.com / Beautiful.ai / modern visual deck lineage. For brand-heavy or design-heavy companies.*

- **Vibe** — Same structural discipline as Sequoia but with brand voice loud. Illustrations, custom type, spatial composition.
- **Substrate** — Brand-tied. Often gradient backgrounds, brand-color section dividers.
- **Display** — Custom or distinctive (Cabinet Grotesk / Migra / Söhne Breit).
- **Components** — Same slide structure as Sequoia, but each slide is composed visually (not just bullet-list-on-bg). Asymmetric layouts. Custom diagrams instead of stock chart styles. Brand illustrations as section openers.
- **Banned** — Letting visual flair displace clarity. If the partner can't get the company in 30 seconds, you have a pretty deck and a no.
- **Pick when** — consumer brand pitch, design-tool pitch, creator economy pitch, anywhere brand IS the moat. **Don't pick** for B2B infra/dev tools — Sequoia-classic wins there.

### `notion-doc-deck` 📄
*Notion-as-deck / Pitch as long-form / written memo. Modern alternative for async fundraising.*

- **Vibe** — Reads like an essay. Long-form prose, screenshots inline, no slide breaks. Investor reads on their own time.
- **Format** — Notion page, Pitch doc, or PDF formatted as a memo. Single column, ~700px wide, body type.
- **Display** — Body-first. Headers exist but don't dominate.
- **Pick when** — async fundraising, deep technical companies, "anti-pitch-deck", founders who write better than they design.
- **Tradeoff** — Hard to skim. Investors who want bullets won't read it. Pick deliberately.

### Disambiguator
| Signal | sequoia-classic | pitch-com-modern | notion-doc |
|---|---|---|---|
| Audience | tier-1 VC partners | brand investors / creator economy funds | technical investors / async readers |
| Format | live presentation | live or share | share only |
| Brand-voice budget | minimal | high | minimal |

---

## 📧 Class: Email / Newsletter
*Inbox-rendered, 600–640px max width, table-based layout for Outlook compat, dark-mode aware.*

### `morning-brew-digest` ☕
*Morning Brew / TLDR / The Hustle lineage. The 2026 default for editorial newsletters.*

- **Vibe** — Magazine-skimmable. Headline + dek + 2 sentences + link. Repeat 5–10 times. Reader scans in 90 seconds.
- **Layout** — Single column 600px. Header band (logo + date + issue#). Section-divider rules between stories. Footer with social links + unsubscribe.
- **Display** — System font stack (`-apple-system, Segoe UI, Helvetica, Arial`) — webfonts unreliable in Outlook. Headlines 22–26px, bold.
- **Body** — 16px, line-height 1.5. Paragraphs short (2–3 sentences max).
- **Components** — Section headers with emoji prefix (☕ MARKETS, 🏛 POLITICS, 🎬 CULTURE). Hairline rules `1px solid #E5E5E5` between sections. Inline links underlined in brand color. "Together with [Sponsor]" callout boxes with light bg.
- **Banned** — Background images (Outlook strips). Web fonts as the *only* font (always include system fallback). HTML >102KB (Gmail clips). Decorative animations.
- **Pick when** — editorial newsletter, daily/weekly digest, news roundup, "Morning Brew-style", "TLDR-style".

### `lenny-substack-essay` ✍️
*Lenny's Newsletter / Stratechery / Substack default. Long-form essay newsletter.*

- **Vibe** — Personal blog post in inbox. One topic, one author voice, 1500–4000 words. Less skimmable, more committed read.
- **Layout** — Single column 600px. Title + author byline + estimated read time. Body text dominant. Inline images. Block quotes. Hairline divider then subscribe CTA.
- **Display** — Serif (Charter / Spectral / system serif fallback) for body — yes serif body in email. Sans for header.
- **Body** — 18px (slightly larger than digest format), line-height 1.6, max-width tighter (560px).
- **Components** — Pull quotes (left-border-accent + larger italic). Inline screenshots with captions. Footnote-style asides. End-of-post subscribe + share CTAs.
- **Banned** — Multi-column layouts. Heavy chrome. Promo banners breaking the read.
- **Pick when** — long-form newsletter, founder writing, analyst publication, "Lenny-style", "Stratechery-style".

### `plain-text-vc` 📝
*Paul Graham / pmarca / classic founder update lineage. Pure text email.*

- **Vibe** — Reads like a personal email because it is. Plain text or near-plain HTML. No header chrome.
- **Layout** — Plain text or minimal HTML. Maybe a single image at top.
- **Components** — Salutation. Paragraphs. Sign-off. That's it.
- **Pick when** — investor update, intimate-list newsletter, founder personal-list, "PG-style", anywhere the *lack* of design IS the design.

### `transactional-product` 🔔
*Stripe / Notion / Linear product transactional emails. Receipts, notifications, summaries.*

- **Vibe** — Branded but minimal. Single primary action. Information-dense but scannable.
- **Layout** — 600px column. Brand mark top. Primary message in 1–2 sentences. Big CTA button. Supporting details below in smaller type.
- **Components** — Bulletproof HTML CTA button (`44×44pt` minimum tap area, table-based for Outlook). Order/event details in a hairline-bordered table. Footer with help link.
- **Banned** — Marketing copy in transactional emails (deliverability hit). Multiple competing CTAs. Decorative images that don't survive image-blocking.
- **Pick when** — receipt, password reset, notification, weekly summary, anything system-triggered.

### Disambiguator
| Signal | morning-brew-digest | lenny-essay | plain-text-vc | transactional |
|---|---|---|---|---|
| Reader commitment | 2 min skim | 10 min read | 1 min read | <30 sec action |
| Author voice | publication brand | individual author | individual person | system |
| Image budget | medium | medium | minimal | minimal |

---

## 📸 Class: Social Static (single image)
*Single-frame post — Instagram square 1080×1080, X/LinkedIn landscape 1200×630, mobile-feed-thumb-sized.*

### `quote-card-editorial` 💬
*The default text-on-photo or text-on-color "quote card" Instagram post.*

- **Vibe** — One quote, one attribution, one brand mark. Stops thumb in feed.
- **Substrate** — Solid brand color OR photographic background with darkening overlay (60–80% opacity gradient bottom-up).
- **Display** — Serif for the quote (DM Serif Display / Playfair / Recoleta), italicized often, 36–56pt.
- **Body** — Sans attribution (Inter 500), 14pt, with em-dash `—`.
- **Components** — Quote text centered or left-aligned, max 18 words. Attribution below with em-dash. Brand mark small bottom-right or top-left. Optional decorative quote-mark glyph at large scale.
- **Banned** — Quotes >25 words (won't fit). Sans-serif for the quote text (looks generic). Multiple competing colors.
- **Pick when** — book quote, podcast pull-quote, manifesto line, "thought leader" post.

### `data-stat-card` 📈
*"One big number" feed post. Common in B2B, fintech, growth-content.*

- **Vibe** — One stat, one label, one source. The number is the whole post.
- **Display** — The stat is HUGE (50%+ of canvas height), tabular-nums, often with `%` or `$` glyph styled smaller.
- **Components** — Stat dominant, label below in 1–2 lines, source attribution at bottom in mono small caps. Optional sparkline or tiny chart.
- **Banned** — Inventing the number. Citing without source. >2 numbers in one post (then it's a chart, different format).
- **Pick when** — case study highlight, market data point, "did you know" content.

### `meme-format-modern` 😂
*Drake-pointing / distracted-boyfriend / two-column-comparison meme formats applied with brand restraint.*

- **Vibe** — Native-feeling humor. Reads in <2 seconds.
- **Components** — Established meme template + brand-relevant text. Don't reinvent the meme — use the format.
- **Banned** — Forcing a brand logo into the meme image. Trying to look "designed" — defeats the meme.
- **Pick when** — community-building post, dev-marketing, "shitpost-with-purpose".
- **⚠️ Warning** — Audience-specific. Works for dev tools, kills luxury brands.

### `announcement-poster-square` 📢
*Product launch, event, milestone — applied to social-square format.*

- **Vibe** — Mini poster optimized for feed.
- **Apply** — Use any of the Class: Poster archetypes (Swiss, Bauhaus, Japanese-minimal, Maximalist) but cropped to 1080×1080 with mobile-readable type sizes (display ≥48pt for thumb-readability).
- **Pick when** — single-image launch announcement, event post, milestone celebration.

### Disambiguator
| Signal | quote-card | data-stat | meme | announcement |
|---|---|---|---|---|
| Content shape | one sentence | one number | template + text | event + date + CTA |
| Tone | thoughtful | factual | humorous | celebratory/urgent |

---

## 🧭 Routing protocol summary

When a brief lands:

1. **Classify by format first.** Carrousel? Landing? Dashboard? Component? Poster? Deck? Email? Social-static?
2. **If ambiguous:** ask the user. One question, single-select. ("Is this a landing page or a SaaS dashboard?")
3. **List specimens in that class.** State them with one-line vibe summaries.
4. **Apply the disambiguator table.** If signals point clearly to one specimen, propose it. If they don't, ask.
5. **Execute the chosen specimen's full body** — substrate, type, components, banned items, motion.
6. **Run the 5-dim self-critique** before emitting.

---

## 📋 Empty classes still to seed (for future versions)

- 🎬 Video thumbnail / cover (YouTube, vertical short)
- 📱 Mobile app screen (single screen, not full flow)
- 🎨 Brand identity system (logo + tokens + applications)
- 🛒 E-commerce product page (different rules from SaaS landing)
- 📰 Long-form article / blog post
- 🖼️ Portfolio case study page

Drop references and we add them.
