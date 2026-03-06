---
name: ui-check
description: >
  Validate AI-generated UI in the browser. Rendered-output integrity checks
  that catch what linters and code review miss. Works with any agent that
  has browser access.
user-invokable: true
---

# ui-check

![llynt — integrity verified](https://raw.githubusercontent.com/llynt/llynt-skills/main/assets/llynt-overflow.gif)

AI agents ship UI faster than anyone reviews it. Linters check source code.
Screenshots need a human. These checks validate the actual rendered output —
what the browser computes, not what the code says.

Paste-and-run browser checks for the regressions that slip past code review.

**Works with:** Claude Code · Cursor · Copilot · Windsurf · v0 · Bolt

---

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
