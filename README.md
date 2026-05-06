# Rensa9 LP

A pre-launch landing page for **Rensa9 (レンサ・ナイン)** — a methodology, not a SaaS — addressing Aggregation Fatigue in the LLM era.

- 🌐 Production: <https://rensa9.ai/>
- 🧱 Parent: [OperationX](https://operationx.jp/) — `合同会社OperationX`
- 🚀 Launch: 2026-06-29
- 🛠 Stack: Static HTML + Vercel (no build step)

---

## Repository structure

```
.
├── index.html             # JP version (canonical) — served at /
├── en/
│   └── index.html         # EN version — served at /en/
├── og.png                 # Open Graph image (1200×630)
├── sitemap.xml            # SEO sitemap
├── robots.txt             # Crawler directives (AI bots welcomed)
├── llms.txt               # Hand-maintained summary for LLM crawlers
├── vercel.json            # Vercel deployment config
├── BESTPRACTICES.md       # Editorial doctrine — read before editing
├── README.md              # This file
├── .gitignore
├── .vercelignore          # Excludes studies/ and docs from deploy
└── studies/               # Internal-only — NOT deployed
    ├── Rensa9_Symbol_Motion_Studies.html
    ├── og-source.html     # Source for regenerating og.png
    └── fonts-archive/     # Self-host fonts (currently unused)
```

---

## Editing rules (TL;DR)

**Read [`BESTPRACTICES.md`](./BESTPRACTICES.md) first.** Every edit should be consistent with the doctrine declared there.

Quick reference:

- 🎨 **Palette is fixed.** Don't introduce new colours. Accent `#0F4392` (Lexus structural blue) appears in only two roles.
- ✍️ **JP is canonical.** EN is its own register, not a literal mirror.
- 🚫 **No marketing verbs.** No exclamation marks. No emoji. Anywhere.
- 📐 **Typography roles are typed.** `--font-logo` (Crimson Pro) / `--font-en` (Spectral) / `--font-jp` (Shippori Mincho B1) / `--font-ui` (Inter). Don't reach outside these.
- 🔁 **When you change copy**, update JSON-LD (`FAQPage` answers) in *both* `index.html` and `en/index.html` so AI crawlers get the same story.
- 🌍 **When you change URLs/structure**, update: canonical tags, hreflang, JSON-LD `@id`, `sitemap.xml`, `llms.txt`, OG `og:url`, footer.

---

## Local preview

No build step. Just serve the directory with any static file server:

```bash
# Option 1: Python (built-in)
python3 -m http.server 8000

# Option 2: Node http-server
npx http-server . -p 8000

# Then open http://localhost:8000
```

To preview the `/en/` route, navigate to `http://localhost:8000/en/`.

> Note: `vercel.json`'s `cleanUrls` and `trailingSlash` rewrites are applied **only on Vercel**, not locally. Local URLs work as-is via `index.html` resolution.

---

## Deploy

Production deploys are automatic on push to `main` via Vercel ↔ GitHub integration.

1. Make changes locally.
2. Commit + push to a feature branch → Vercel creates a preview URL automatically.
3. Open a PR. Review the preview.
4. Merge to `main` → live within ~30s.

**Important:** any change to copy on the page should also update the matching JSON-LD `FAQPage` blocks. AI crawlers compare the two.

---

## Regenerating `og.png`

The OG image is hand-rendered from `studies/og-source.html`:

1. Open `studies/og-source.html` in a browser at exactly 1200×630.
2. Take a clean screenshot (no browser chrome).
3. Save as `/og.png` at the repo root.
4. Commit. Both LP files reference `https://rensa9.ai/og.png`.

Update whenever the launch date or tagline changes.

---

## Channels (the only outbound CTAs until launch)

- **note** — long-form Japanese essays: <https://note.com/rensa9>
- **X / Twitter** — short signals: <https://x.com/rensa9_ai>

No email capture, no Discord, no waitlist form.

---

## Related

- [`llms.txt`](./llms.txt) — AI-crawler-friendly summary
- [`robots.txt`](./robots.txt) — explicit allow-list for major AI crawlers
- [`BESTPRACTICES.md`](./BESTPRACTICES.md) — editorial doctrine

---

© 2026 OperationX
