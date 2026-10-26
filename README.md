# Claude Code Toolkit

[![CI](https://github.com/Zhiyilang/claude-code-toolkit/actions/workflows/verify.yml/badge.svg)](https://github.com/Zhiyilang/claude-code-toolkit/actions/workflows/verify.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

A small, zero-dependency collection of drop-in tools that make **Claude Code** (and any agentic coding setup) safer, faster, and more reviewable.

Every tool is:
- **Zero external dependencies** — pure `bash` / Python **stdlib**.
- **Tested** — each ships with a usage example or a real sample output.
- **Safe by default** — nothing here phones home, deletes anything, or needs an API key.

## What's inside

| Tool | What it does | Stack |
|------|-------------|-------|
| [`changelog-skill/`](changelog-skill) | Generate a structured `CHANGELOG.md` from git history, auto-categorizing commits into Added / Fixed / Changed / Removed / Docs. | bash |
| [`claude-md-template/`](claude-md-template) | A production-ready `CLAUDE.md` template for **Next.js 15 (App Router) + SQLite** projects. | Markdown |
| [`security-hook/`](security-hook) | A PreToolUse hook that **blocks destructive commands** (`rm -rf`, `git push --force`, data-loss SQL) before they run, while allowing everything else. | Python |
| [`pr-review-agent/`](pr-review-agent) | A CLI + GitHub Action that produces a structured PR review (risk flags, suggestions, confidence) with **no LLM key required**. | Python |

## Quick start

```bash
# 1) CHANGELOG generator
bash changelog-skill/changelog.sh -o CHANGELOG.md

# 2) Drop the Next.js+SQLite CLAUDE.md into your project
cp claude-md-template/CLAUDE.md /path/to/your/project/CLAUDE.md

# 3) Install the destructive-command guard
python3 security-hook/install.py

# 4) Review a PR (set GITHUB_TOKEN first)
export GITHUB_TOKEN=ghp_xxx
python3 pr-review-agent/claude-review.py --pr owner/repo#123
```

Each subdirectory has its own README with full details and samples.

## Why this exists

These were originally built as solutions to public developer-tooling bounties, then
consolidated here as a single, coherent, reusable toolkit. Use them as-is, or as a
starting point for your own agentic workflow.

## License

MIT — see [LICENSE](LICENSE).
