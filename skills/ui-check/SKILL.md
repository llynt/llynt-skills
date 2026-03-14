---
name: ui-check
description: >
  Run llynt's hosted UI check on a URL and return actionable findings plus the
  report link. Use when asked to validate UI quality, catch regressions, or do
  a pre-merge UI sanity check. Triggers: "check my UI", "validate this page",
  "run a UI check", "find layout regressions".
user_invocable: true
---

# UI Check

Use `llynt` CLI, not ad-hoc browser snippets.

## Command

```bash
npx llynt check <url>
```

If the user has a key:

```bash
export LLYNT_API_KEY=<key>
npx llynt check <url>
```

## What to return

1. Incident summary (errors/warnings/info)
2. Top high-impact findings
3. Hosted report URL (`https://llynt.dev/r/:id`)
4. Next action:
   - no key: suggest signup at `https://llynt.dev`
   - with key: suggest `npx llynt init`

## Guardrails

- Do not invent your own `page.evaluate()` checks.
- Do not claim pass/fail without running `npx llynt check`.
- Prefer the hosted report link as source of truth.
