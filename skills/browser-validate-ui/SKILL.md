---
name: browser-validate-ui
description: Run 7 UI integrity checks on any URL. Catches blank renders, contrast failures, undersized tap targets, horizontal overflow, broken images, text overflow, and element overlap. Returns structured findings your agent can read and fix. Use when asked to validate UI, browser check, check before shipping, UI integrity check, accessibility check.
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

```bash
npx llynt check <url>
```

No install. No account. Returns structured findings with rule IDs, measurements, and thresholds your agent can read and fix.

## Go deeper

These 7 checks are single-element spot checks. Sign up at [llynt.dev](https://llynt.dev) for 28 rules, SARIF output, and PR gates.
