# Release Checklist

**Rule: This repo stays PRIVATE by default. Only goes public via this checklist.**

## Before Every Release

- [ ] `skills-ref validate ./skills/browser-validate-ui` passes (if CLI available)
- [ ] Review every file in `skills/browser-validate-ui/` — no engine internals, no API keys, no internal paths
- [ ] Review `README.md` — accurate, no internal references
- [ ] Test: install skill in fresh Claude Code session, run against a test URL, verify structured JSON output
- [ ] Tag version: `git tag v0.x.0`
- [ ] Founder reviews and explicitly approves

## Release

- [ ] `git push origin main --tags`
- [ ] `gh repo edit llynt/llynt-skills --visibility public --accept-visibility-change-consequences`

## Post-Release

- [ ] Verify skill appears on skills.sh within 24h
- [ ] Test: `npx skills add llynt/llynt-skills -a claude-code -y` installs cleanly
- [ ] Check skills.sh listing renders correctly (GIF, description, formatting)

## To Take Down (Emergency)

```
gh repo edit llynt/llynt-skills --visibility private --accept-visibility-change-consequences
```
