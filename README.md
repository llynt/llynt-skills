# llynt-skills

Free UI quality checks for AI coding agents.

Built by [llynt](https://llynt.dev) — catch expensive UI breakage before merge.

## Install

```bash
# All agents (Claude, Cursor, Codex, etc.)
npx skills add llynt/llynt-skills -a '*' -y
```

## Included Skill

### `browser-validate-ui`

Runs the real hosted checker via CLI:

```bash
npx llynt check <url>
```

What you get:
- Incident-first summary in terminal
- Hosted report URL (`llynt.dev/r/:id`)
- Anonymous mode with no key, full mode with `LLYNT_API_KEY`

## Quick start

```bash
npx llynt check https://example.com
```

For full rules and higher limits:

```bash
export LLYNT_API_KEY=<your-key>
npx llynt check https://example.com
```

## License

MIT
