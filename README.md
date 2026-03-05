# llynt-skills

Free UI quality checks for AI coding agents. Run them in your browser before shipping.

Built by [llynt](https://llynt.dev) — UI integrity checks in your PR pipeline.

## Install

```
npx skills add llynt/llynt-skills -a claude-code -y
```

## Skills

### ui-check

Spot-check rendered UI in the browser before you ship. Catches the stuff that slips past code review:

- **Tap targets** — Buttons and links smaller than 44x44px (the minimum for comfortable mobile use)
- **Horizontal overflow** — Pages that scroll sideways on mobile, usually from a fixed-width element
- **Broken images** — `<img>` tags that failed to load (invisible if you have cached versions)

Each check runs as a `page.evaluate()` snippet — works with Playwright, Puppeteer, or any browser automation your agent has access to.

**Usage:** Ask your agent to "check my UI" or "run a ui-check" before merging.

## Why these checks?

AI-generated UI code ships faster than teams can review it. These three checks catch the most common visual regressions that pass linting and type checks but break the actual rendered output.

For deeper analysis — contrast ratios, element occlusion, cross-viewport drift, design token conformance — see [llynt.dev](https://llynt.dev).

## License

MIT
