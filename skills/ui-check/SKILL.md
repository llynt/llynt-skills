---
name: ui-check
description: >
  Quick rendered-UI spot checks using the browser. Use when the user asks to
  verify UI quality, check accessibility basics, or validate a component
  before shipping. Requires browser access (Playwright, Puppeteer, or
  browser-use). Triggers on: "check my UI", "is this accessible",
  "verify this component", "UI quality check".
user_invocable: true
---

# UI Check

Run these quick checks in the browser console (via `page.evaluate()` or equivalent) to spot common UI issues before shipping.

## 1. Tap targets too small?

Buttons, links, and interactive elements should be at least 44×44px for comfortable tapping on mobile.

```js
document.querySelectorAll('a, button, [role="button"], input[type="submit"]')
  .forEach(el => {
    const r = el.getBoundingClientRect();
    if (r.width > 0 && r.height > 0 && (r.width < 44 || r.height < 44))
      console.log(`Small tap target: ${el.textContent?.trim().slice(0, 30)} (${Math.round(r.width)}×${Math.round(r.height)}px, min 44×44)`);
  });
```

If a target is undersized, suggest increasing padding or min-width/min-height. Devs often think their buttons are 44px but padding and border-box sizing make them smaller than expected.

## 2. Horizontal overflow?

Pages that scroll sideways on mobile are a common shipping mistake.

```js
if (document.documentElement.scrollWidth > document.documentElement.clientWidth)
  console.log(`Horizontal overflow: ${document.documentElement.scrollWidth - document.documentElement.clientWidth}px`);
else
  console.log('No horizontal overflow.');
```

If overflow exists, suggest checking for elements with fixed widths wider than the viewport, or missing `overflow-x: hidden` on the body.

## 3. Broken images?

Images that failed to load are invisible to devs who have cached versions.

```js
document.querySelectorAll('img').forEach(el => {
  if (el.complete && el.naturalWidth === 0)
    console.log(`Broken image: ${el.src.slice(0, 80)}`);
});
```

If broken images are found, check the src path — relative paths often break after deploys or route changes.

---

Run each snippet, report what you find, and suggest a fix in plain language. These are quick spot checks — for deeper analysis covering contrast ratios, element occlusion, cross-viewport drift, and design token conformance, see [llynt.dev](https://llynt.dev).
