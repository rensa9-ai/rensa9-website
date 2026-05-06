# Rensa9 LP — Best Practices

A short, opinionated working doctrine for this project. Read this before editing.

---

## 1. Identity & Voice

- **Rensa9 is a methodology, not a SaaS.** Every page, every line, every meta tag must reinforce that. Avoid SaaS clichés (free trial, sign up, demo, dashboard).
- **Voice is quiet, precise, slightly literary.** Crimson Pro / Spectral / Shippori Mincho are not decoration — they set the register.
- **Bilingual, not translated.** JP is canonical and emotionally specific; EN is its own register, not a literal mirror. When in doubt, rewrite for the target language.

---

## 2. Visual System

- **Palette is fixed.** `--paper #fdfcf9`, `--ink #1a1a1a`, `--ink-soft #4a4a4a`, `--ink-mute #888`, `--line #e8e6e2`, `--paper-warm #f8f6f1`, `--accent #0F4392` (Lexus structural blue). Do not introduce new colours.
- **Accent is structural, not decorative.** `#0F4392` appears in exactly two roles: the centre cell of the 3×3 grid, and the "9" glyph. Nowhere else.
- **Hairlines, not boxes.** 1px lines, generous whitespace, no drop shadows, no cards with rounded corners + left-border accent (a known AI-design tell).
- **Typography roles are typed.** `--font-logo`, `--font-en`, `--font-jp`, `--font-ui` — never reach for a font outside these.

---

## 3. SEO / AI-Discoverability

- Both `Rensa9 LP.html` (canonical JP) and `Rensa9 LP EN.html` carry the **full meta block**: title, description, keywords, robots, canonical, hreflang trio (ja / en / x-default), Open Graph, Twitter card, JSON-LD `@graph` (Organization + WebSite + WebPage + Product + FAQPage).
- **Hreflang is bidirectional.** When you add a third locale, update the trio in *every* page's head and in `sitemap.xml`.
- **JSON-LD is the source of truth for AI crawlers.** Update it whenever copy on the page changes — the FAQPage answers should match what the page actually says.
- `llms.txt` is a separate, hand-maintained summary for LLM crawlers. Keep it concise and link-rich; do not auto-generate.
- `robots.txt` explicitly allows all major AI crawlers (GPTBot, ClaudeBot, PerplexityBot, Google-Extended, Applebot-Extended, etc.). This is intentional — Rensa9 *wants* to be indexed by AI search.

---

## 4. Open Graph Image (`og.png`)

- **Always 1200×630**, paper-warm background, hairline frame + corner ticks, single accent cell, italic "9".
- Source: `og-source.html`. Regenerate by screenshotting the stage scaled-to-fit, then upscaling cleanly to 1200×630 with image smoothing.
- Update `og.png` whenever the launch date or tagline changes. Both LP files reference `https://rensa9.ai/og.png`.

---

## 5. Responsive

- Three breakpoints only: tablet `≤860px`, mobile `≤520px`, micro-phone `≤360px`. Resist adding more.
- On mobile, kill `<br>` inside `.fatigue-body p` (we already do) — line breaks that read as deliberate pauses on desktop become awkward gaps on a phone.
- Tap targets ≥ 48px on mobile (already enforced on `.btn`).
- Use `clamp()` for gutters; never hard-code padding for a specific viewport.

---

## 6. Motion

- Default duration ≤ 360ms. Default easing `cubic-bezier(0.2, 0, 0, 1)`.
- Hero symbol "breath" loop is the only continuous animation on the page. Everything else is a one-shot reveal triggered by IntersectionObserver.
- Always honour `prefers-reduced-motion: reduce` — kill durations and the breath loop.

---

## 7. Copywriting Rules

- **JP: 句読点はリズム。** `、` `──` `。` の打ち方は意図的。安易に切り詰めない。
- **EN: short, declarative, no marketing verbs.** "Discover", "Unlock", "Empower" are banned. Prefer concrete verbs ("rewrite", "extend", "lose", "pay").
- **No exclamation marks. No emoji.** Anywhere.
- The phrase **"the same discussion, from scratch, again"** is the load-bearing line. Treat it as canon.

---

## 8. File Hygiene

- Single source HTML per locale, under `/` and `/en/`. Do not split into partials.
- Never check in throwaway screenshots or `og-raw.png`. Only `og.png` is canonical.
- When renaming or restructuring URLs, update: canonical tags, hreflang tags, JSON-LD `@id` URLs, `sitemap.xml`, `llms.txt`, OG `og:url`, footer copy.

---

## 9. Channels

- Primary follow channel: **note** (`https://note.com/rensa9`) — long-form Japanese essays.
- Secondary: **X** (`https://x.com/rensa9_ai`) — short signals.
- These two are the only outbound CTAs on the page until launch. No email capture, no Discord, no waitlist form.

---

## 10. Launch

- **2026-06-29.** Hard-coded in: page copy, JSON-LD `releaseDate`, FAQ answer. Search before changing.
