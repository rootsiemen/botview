# Contributing to BotView

Thanks for helping make the web more visible to AI. BotView is a single-file
Python tool (`botview.py`) with zero dependencies — contributions should keep
it that way: standard library only, Python 3.8+.

## Getting started

```bash
git clone https://github.com/rootsiemen/botview
cd botview
python3 botview.py audit https://example.com
```

No build step, no virtualenv, no pip install. If it needs a dependency, it
doesn't belong in BotView.

## How it works

Everything ships in `botview.py`:

- `fetch()` — retrieves a page (urllib, with a `curl` fallback)
- `PageParser` — an `HTMLParser` subclass that extracts the title, meta
  description, canonical, H1s, JSON-LD schema types and readable text
- `parse_robots()` — reads `robots.txt` and reports the status of each major
  AI crawler (GPTBot, ChatGPT-User, ClaudeBot, Claude-Web, PerplexityBot,
  Google-Extended, CCBot, Bytespider)
- `audit()` — runs every check and computes the AI Visibility Score
- `view()` — prints the page as plain text, the way an LLM reads it
- `generate()` — builds an `llms.txt` draft from the site's sitemap

## Adding a new check

1. Add the check inside `audit()` in `botview.py`, following the existing
   `add(...)` pattern: a plain-English name, a pass/fail condition, a short
   detail string, and a points value. Keep the total at 100.
2. Make sure the check also appears in `--json` output (it will, if you use
   `add()`).
3. Test it against at least two or three real sites — including one that
   should pass and one that should fail — and include the before/after scores
   in your PR description.
4. False positives are the enemy: when in doubt, make the check *more*
   precise, not louder.

## Reporting bugs and false positives

A wrong score is a bug. Open an issue with the *Bug report* template and
include the site URL and the check that scored incorrectly — that case
usually becomes a regression test.

## Pull requests

- One check or one fix per PR; small PRs get reviewed the same day.
- Keep the single-file design: everything ships in `botview.py`.
- By contributing you agree to the [Code of Conduct](CODE_OF_CONDUCT.md) and
  that your contribution is licensed under the project's MIT license.
