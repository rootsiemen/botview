# 👁️ BotView

**See your website the way AI sees it.**

BotView is a zero-dependency, single-file Python tool that audits any website
for **AI visibility** — how well ChatGPT, Claude, Perplexity and other AI
systems can find, read, understand and cite your site. It checks your
`llms.txt`, your AI-crawler rules, your structured data and the on-page basics
an LLM depends on, then gives you a single **AI Visibility Score out of 100**.

No pip install. No API keys. No SaaS dashboard. Just Python 3 and one file.

```bash
python3 botview.py audit https://igaf.me
# 🔍 BotView audit — https://igaf.me
#    AI Visibility Score: 90/100
```

## Why AI visibility?

Search is changing. A growing share of your visitors now arrive through AI
answers, not blue links — and AI models can only cite what they can crawl,
parse and understand. Sites that block AI crawlers in `robots.txt`, skip
`llms.txt`, or ship pages with almost no readable text are invisible to that
traffic.

BotView tells you exactly where you stand, in one command.

## Features

### `audit` — AI Visibility Score /100

Scores a site across everything an AI crawler cares about:

- **`llms.txt`** — present, valid, and linking to your key pages
- **`llms-full.txt`** — the full-content companion file
- **AI-crawler rules in `robots.txt`** — checked individually for GPTBot,
  ChatGPT-User, ClaudeBot, Claude-Web, PerplexityBot, Google-Extended,
  CCBot and Bytespider: is each one blocked?
- **Structured data** — JSON-LD schema types found on the page
- **On-page basics** — title tag, meta description, canonical URL, exactly
  one H1
- **Readable text ratio** — how much of the page an LLM can actually read
  versus markup and scripts
- **Sitemap** — present and populated

### `view` — the page as an LLM reads it

Prints the page as plain text: no CSS, no scripts, no layout — the raw
content an AI model actually gets. Often a shock the first time you run it.

### `generate` — an `llms.txt` draft in seconds

Builds a ready-to-edit `llms.txt` for your site from its sitemap, so you can
go from "no `llms.txt`" to "published" in minutes.

## Usage

```bash
# Audit a site (human-readable report)
python3 botview.py audit https://example.com

# Audit with machine-readable output, for scripts and CI
python3 botview.py audit https://example.com --json

# See a page the way an LLM sees it
python3 botview.py view https://example.com

# Generate an llms.txt draft from the sitemap
python3 botview.py generate https://example.com > llms.txt
```

## Real-world scores

Verified runs against live sites:

| Site | AI Visibility Score |
|------|--------------------:|
| [igaf.me](https://igaf.me) | **90/100** |
| [frinjo.me](https://frinjo.me) | **82/100** |

Run it on your own site — then fix what it flags and watch the score climb.

## Requirements

- Python 3.8+
- Nothing else. Standard library only, zero dependencies.

## Contributing

Contributions are welcome — new checks, better parsing, fewer false
positives. See [CONTRIBUTING.md](CONTRIBUTING.md) and the
[Code of Conduct](CODE_OF_CONDUCT.md).

## License

MIT — see [LICENSE](LICENSE).

## Author

**Muhamad Raza Haider** — [@rootsiemen](https://github.com/rootsiemen)

BotView is built and maintained by a solo open source developer. If it helped
your site get seen by AI, a ⭐ on the repo goes a long way.
