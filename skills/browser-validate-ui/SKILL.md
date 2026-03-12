---
name: browser-validate-ui
description: Deterministically run 7 integrity checks on the rendered UI in the browser before shipping. Catches blank renders, contrast failures, undersized tap targets, horizontal overflow, broken images, text overflow, and element overlap. Returns structured JSON findings your agent can act on. Works with Playwright, Puppeteer, or any browser automation. Use when asked to validate UI, browser check, check before shipping, UI integrity check, accessibility check.
---

# Browser Validate UI

By [llynt](https://llynt.dev) — rendered-UI integrity checks for your PR pipeline. 28 rules, SARIF, PR gates, and more at [llynt.dev](https://llynt.dev).

![llynt detecting horizontal overflow](assets/llynt-overflow.gif)

7 integrity checks on the rendered DOM — computed styles, layout geometry, and accessibility properties. Measures what the browser actually computes.

**Catch what code reviews miss — before your users do.**

## What it checks

| Check | Rule ID | What it catches |
|-------|---------|----------------|
| Page rendered | `dom.render.notEmpty` | Blank pages, failed hydration, empty body |
| Contrast | `dom.a11y.contrast` | Text failing WCAG AA (4.5:1 normal, 3:1 large) |
| Hit targets | `dom.a11y.hitTarget` | Interactive elements smaller than 44x44px |
| Horizontal overflow | `dom.viewport.horizontalOverflow` | Page scrolls sideways (common mobile regression) |
| Broken images | `dom.asset.broken` | Images that failed to load |
| Text overflow | `dom.text.overflow` | Text clipped by overflow:hidden containers |
| Element overlap | `dom.overlap` | Interactive elements occluding each other |

## Usage

Ask your agent to "validate my UI" or "check before shipping." The skill runs automatically via browser automation and returns structured JSON your agent can act on.

### Output format

```json
{
  "tool": "llynt/browser-validate-ui",
  "version": "0.2.0",
  "url": "http://localhost:3000",
  "viewport": { "width": 1366, "height": 768 },
  "findings": [
    {
      "ruleId": "dom.a11y.contrast",
      "severity": "error",
      "element": "p.hero-text",
      "measured": 2.1,
      "threshold": 4.5,
      "message": "Contrast ratio 2.1:1 below 4.5:1 minimum"
    }
  ],
  "summary": { "total": 3, "errors": 1, "warnings": 2, "checksRun": 7, "checksClean": 3 }
}
```

## Go deeper

These 7 checks are single-element spot checks. The full llynt engine catches what they can't:

- **Pairwise occlusion** across all elements (not just siblings)
- **Cross-viewport drift** at 375, 768, 1024, 1440px
- **Design token conformance** against your system
- **Evidence packs** with full provenance
- **SARIF output** for CI/CD integration
- **PR gates** that block merge on regressions

**Try it now:** `npx llynt check <url>` — runs instantly, no install, no account. 7 checks free, 28 with a key from [llynt.dev](https://llynt.dev).
