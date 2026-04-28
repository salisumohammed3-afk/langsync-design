# LangSync Design

**By [LangSync](https://langsync.ai)**

Extract a **DESIGN.md** from any website. Following [Google's open DESIGN.md standard](https://github.com/google-labs-code/design.md).

LangSync Design is a Next.js app: paste a URL, capture a viewport screenshot via Hyperbrowser, scrape structured page content, and send both to **Claude Opus 4.7** for a combined visual + structural analysis. The result is a single `DESIGN.md` with YAML frontmatter (tokens) and markdown sections, plus an on-page preview of colors, type, spacing, and radius.

Forked from the open-source [HyperDesign](https://github.com/hyperbrowserai/hyperbrowser-app-examples/tree/main/hyperdesign) example by Hyperbrowser, rebranded for LangSync.

## Get API keys

- [Hyperbrowser](https://hyperbrowser.ai)
- [Anthropic](https://console.anthropic.com)

## Quick start

```bash
npm install
cp .env.example .env.local
```

Add `HYPERBROWSER_API_KEY` and `ANTHROPIC_API_KEY` to `.env.local`, then:

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000).

## How it works

1. **Screenshot** — Stealth Hyperbrowser session; Playwright connects over CDP; viewport PNG only (not full page).
2. **Scrape** — Hyperbrowser `scrape.startAndWait` with markdown and `onlyMainContent: false` for broader style context.
3. **Analyze** — Opus 4.7 receives the image + scraped text and emits **DESIGN.md** only.
4. **Preview** — The API parses YAML frontmatter into `tokens` for the visual panel; raw markdown is shown with line numbers.

## Tech

- Next.js App Router, Tailwind CSS v4, TypeScript
- `@hyperbrowser/sdk`, `playwright`, `@anthropic-ai/sdk`
- Spec: [google-labs-code/design.md](https://github.com/google-labs-code/design.md)

## License

MIT
