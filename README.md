# Agent Smart Fetch

Better web fetching for agents.

## Features

- 🔐 **Browser-like TLS/SSL + HTTP fingerprints** — better success on bot-defended pages
- 🧹 **Defuddle extraction** — clean readable content instead of noisy HTML
- 🧠 **Useful metadata** — title, author, site, language, published date when available
- 📦 **Downloads + large file support** — stream attachments and binaries to temp files
- ⚡ **Batch fetch** — fetch many URLs with bounded concurrency
- 📝 **Multiple output formats** — `markdown`, `html`, `text`, `json`

## [pi-smart-fetch](./packages/pi-smart-fetch/README.md)

Smart Fetch for pi.dev.

Registers:
- `web_fetch`
- `batch_web_fetch`

## [openclaw-smart-fetch](./packages/openclaw-smart-fetch/README.md)

Smart Fetch for OpenClaw.

Registers:
- `smart_fetch`
- `batch_smart_fetch`

![pi Smart Fetch](https://raw.githubusercontent.com/Thinkscape/agent-smart-fetch/main/packages/pi-smart-fetch/demo.gif)

## Development

This repo is a Bun monorepo.

Install dependencies:

```bash
bun install
```

Run the workspace:

```bash
bun run test
bun run build
bun run check
```

Run package-specific commands:

```bash
bun run test:core
bun run test:pi
bun run test:openclaw

bun run build:core
bun run build:pi
bun run build:openclaw
```

Integration tests:

```bash
bun run test:integration
```

Install the local pre-commit hook:

```bash
bun run hooks:install
```

## Versioning and publishing

Versioning is global across the monorepo.

Bump all package versions together:

```bash
bun run version:patch
bun run version:minor
bun run version:major
```

Create a release commit and tag:

```bash
bun run release
```

Local manual publish commands:

```bash
bun run publish:pi
bun run publish:openclaw
bun run publish:all
```

Note: development uses Bun, but CI publishing still uses `npm publish` so npm Trusted Publishing works correctly.

## Repository

- GitHub: `https://github.com/Thinkscape/agent-smart-fetch`
