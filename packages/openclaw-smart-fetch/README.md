# openclaw-smart-fetch

`openclaw-smart-fetch` adds smarter web fetching tools to OpenClaw.

## Features

- 🔐 **Browser-like TLS/SSL + HTTP fingerprints** — better success on bot-defended pages
- 🧹 **Defuddle extraction** — clean readable content instead of noisy HTML
- 🧠 **Useful metadata** — title, author, site, language, published date when available
- 📦 **Downloads + large file support** — stream attachments and binaries to temp files
- ⚡ **Batch fetch** — fetch many URLs with bounded concurrency
- 📝 **Multiple output formats** — `markdown`, `html`, `text`, `json`

## Supported sites

- **Anything fetchable over server-side HTTP** — this package is not limited to a fixed allowlist
- Docs, blog posts, articles, and knowledge-base pages
- Reddit posts and comment threads
- X / Twitter posts
- YouTube pages and transcripts
- GitHub pages, issues, PRs, and discussions
- Hacker News threads
- Substack posts
- Pages with code blocks, footnotes, math, and callouts

Notes:
- Defuddle is the cleanup layer: it strips common page chrome like nav, sidebars, related links, share widgets, and footers
- It does **not** execute JavaScript or solve interactive anti-bot/login flows

## Install

From npm:

```bash
openclaw plugins install openclaw-smart-fetch
```

From a local checkout:

```bash
openclaw plugins install -l /absolute/path/to/agent-smart-fetch/packages/openclaw-smart-fetch
```

## OpenClaw tools

Registers:
- `smart_fetch`
- `batch_smart_fetch`

Synopsis:

```text
smart_fetch(url, browser?, os?, headers?, maxChars?, timeoutMs?, format?, removeImages?, includeReplies?, proxy?)
batch_smart_fetch(requests)
```

For `batch_smart_fetch`, each item in `requests` accepts the same parameters as `smart_fetch`.

## Output formats

| Format | What you get |
|---|---|
| `markdown` | Best default for readable page content |
| `html` | Cleaned HTML output |
| `text` | Plain text with markdown stripped |
| `json` | Structured JSON for metadata-heavy workflows |

## Plugin defaults

See `openclaw.plugin.json` for the schema. The effective defaults are:

```json
{
  "maxChars": 50000,
  "timeoutMs": 15000,
  "browser": "chrome_145",
  "os": "windows",
  "removeImages": false,
  "includeReplies": "extractors",
  "batchConcurrency": 8,
  "tempDir": "/tmp/openclaw-smart-fetch"
}
```

| Setting | Default | Description |
|---|---:|---|
| `maxChars` | `50000` | Default maximum returned characters |
| `timeoutMs` | `15000` | Default request timeout in milliseconds |
| `browser` | `chrome_145` | Default browser fingerprint profile |
| `os` | `windows` | Default OS fingerprint profile |
| `removeImages` | `false` | Strip image references by default |
| `includeReplies` | `extractors` | Include replies/comments only when site extractors support them |
| `batchConcurrency` | `8` | Default bounded concurrency for `batch_smart_fetch` |
| `tempDir` | OS temp dir | Directory for attachment and binary downloads |

## Dev and publishing note

This repo uses Bun for local development, tests, and workspace scripts. Package publishing still goes through `npm publish` in CI so npm Trusted Publishing can be used.
