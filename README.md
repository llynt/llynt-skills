# llynt-skills

Rendered-UI integrity checks for AI coding agents. Measure what the browser actually computes — not what the source code says.

Built by [llynt](https://llynt.dev) — UI integrity checks in your PR pipeline.

## Install

```
npx skills add llynt/llynt-skills
```

## Skills

### browser-validate-ui

Run 7 rendered-UI integrity checks in the browser before shipping. Returns structured JSON findings your agent can act on — not advice, not guidelines.

- **Page rendered** — Catches blank pages, error states, empty renders
- **Contrast** — Text failing WCAG AA contrast ratio
- **Hit targets** — Interactive elements smaller than 44x44px
- **Horizontal overflow** — Pages that scroll sideways on mobile
- **Broken images** — `<img>` tags that failed to load
- **Text overflow** — Content clipped by overflow:hidden containers
- **Element overlap** — Interactive elements occluding each other

Each check runs via `page.evaluate()` — works with Playwright, Puppeteer, or any browser automation.

**Usage:** Ask your agent to "validate my UI" or "browser check" before merging.

## How is this different?

Most UI skills give your agent guidelines to follow. This one **measures the rendered DOM** and returns structured findings with rule IDs, measurements, and thresholds. Your agent doesn't interpret — it reads the result and fixes what failed.

Want more? `npx llynt check <url>` — runs instantly, no install. 7 checks free, 28 with a key from [llynt.dev](https://llynt.dev).

## License

MIT
