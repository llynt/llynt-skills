---
name: browser-validate-ui
description: Run 7 UI integrity checks on any URL. Catches blank renders, contrast failures, undersized tap targets, horizontal overflow, broken images, text overflow, and element overlap. Returns structured findings your agent can read and fix. Use when asked to validate UI, browser check, check before shipping, UI integrity check, accessibility check.
---


![llynt detecting horizontal overflow](assets/orig-single-logo.gif)

# [llynt](https://llynt.dev)


## Browser Validate UI

- UI integrity checks for your PR pipeline.

- Measures what the browser shows users, not just what the code says.


No install. No account. Runs a real browser (playwright) against any URL. Returns structured findings with rule IDs, measurements, and thresholds your agent can read and fix. 

# HOW TO 

## CALL
```bash
# check url w/ html report
npx llynt check <url>

# check url w/ html report + json for agent to read
npx llynt check <url> --json
```

## RESPONSE
```bash

  26 of 26 rules checked
  Capturing... 2 viewports (360px, 768px)
  Analyzing... XXX nodes, XXX cost units

  XX incidents (XX evidence points) across 2 viewports
    X errors · XX warnings · XX info

  Open full report:
    https://llynt.dev/r/RANDOM_GUID
    Expires <WEEK FROM RESPONSE TIME>

  Details are in the report link above.
  For machine-readable findings, re-run with --json.

  XX more incidents found with full analysis — sign up at llynt.dev

  Want full SARIF evidence + agent-ready fixes?
  Set up the PR gate — your agent can do it:
    npx llynt init --github
```

What you get:
- Incident-first summary in terminal
- Hosted report URL (`llynt.dev/r/:id`)
- Anonymous mode with no key, full mode with `LLYNT_API_KEY`

## Quick start

For full rules and higher limits sign up at llynt.dev:

```bash
export LLYNT_API_KEY=<your-key>
npx llynt check https://example.com
```

> &nbsp;
> ### Catch what code reviews miss
> ### &emsp;&emsp;&emsp;&emsp; &emsp;&emsp; — before your users do.
> &nbsp;



## Go deeper

- These 7 checks are single-element spot checks.
- For 26 more free rules and access to PR gates and SARIF reports, sign up at [llynt.dev](https://llynt.dev)


## What it checks

| Check | Rule ID | What it catches |
|-------|---------|----------------|
| Element overlap | `dom.overlap` | Interactive elements occluding each other |
| Contrast | `dom.a11y.contrast` | Text failing WCAG AA (4.5:1 normal, 3:1 large) |
| Hit targets | `dom.a11y.hitTarget` | Interactive elements smaller than 44x44px |
| Horizontal overflow | `dom.viewport.horizontalOverflow` | Page scrolls sideways (common mobile regression) |
| Broken images | `dom.asset.broken` | Images that failed to load |
| Text overflow | `dom.text.overflow` | Text clipped by overflow:hidden containers |
| Page rendered | `dom.render.notEmpty` | Blank pages, failed hydration, empty body |
