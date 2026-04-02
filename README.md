<div align="center" id="readme-top">

<!-- BANNER: 替换为你的 banner 图片 -->
![Revolve Banner][banner]

[![License][license-badge]][license]
[![Claude Code][claude-badge]][claude-code]
[![Plugin][plugin-badge]][install-url]

**Self-Evolving AI Research Architecture for Claude Code**

Research topics via NotebookLM, store in Obsidian, evolve CLAUDE.md from accumulated experience.

[Quick Start][quick-start] •
[Skills Reference][skills-ref] •
[Sync Script][sync-section] •
[Configuration][config-section]

[![English][lang-en-badge]][lang-en]
[![简体中文][lang-zh-badge]][lang-zh]

</div>

<br>

<details open>
<summary><kbd>Table of Contents</kbd></summary>

- [How It Works][how-it-works]
- [Prerequisites][prerequisites]
- [Installation][installation]
- [Quick Start][quick-start]
- [Skills Reference][skills-ref]
- [Sync Script][sync-section]
- [Templates][templates-section]
- [Configuration][config-section]
- [Contributing][contributing]
- [License][license-section]

</details>

<br>

## How It Works

<!-- DIAGRAM: 替换为你的飞轮架构图 -->
![Flywheel Diagram][flywheel-diagram]

```
Collect              Analyze            Store             Evolve
────────────         ──────────         ───────           ──────────────
YouTube / Web   →    NotebookLM    →    Obsidian    →    CLAUDE.md    →  Better AI
PDF / Text           (free Google AI)   (your vault)     (append-only)    └── loop
```

Each research session feeds back into your AI — making the next session smarter. The flywheel closes automatically with Revolve's evolution skill, or manually by reviewing your notes and updating CLAUDE.md.

<div align="right">

[![][back-to-top]][readme-top]

</div>

## Prerequisites

| Dependency | Required | Install |
|------------|----------|---------|
| [Claude Code][claude-code] | Yes | — |
| [Obsidian][obsidian] vault | Yes | — |
| NotebookLM MCP server | Yes | `pipx install notebooklm-mcp-cli` then `nlm login` |
| yt-dlp | Yes (YouTube) | `brew install yt-dlp` or `pip install yt-dlp` |
| defuddle | Optional | `npm install -g @nicekate/defuddle` |
| Python 3.8+ | Yes (sync script) | Pre-installed on macOS |
| fswatch | Optional (auto-sync) | `brew install fswatch` |

<div align="right">

[![][back-to-top]][readme-top]

</div>

## Installation

```bash
claude plugin marketplace add https://github.com/eisen0419/revolve
claude plugin install revolve
```

<div align="right">

[![][back-to-top]][readme-top]

</div>

## Quick Start

```bash
# 1. Configure vault path and check dependencies
/revolve-setup

# 2. Search YouTube
/yt-search "Claude Code tips"

# 3. Full research pipeline → NotebookLM analysis → Obsidian note
/research-pipeline youtube "AI productivity"

# 4. Evolve CLAUDE.md from accumulated experience
/evolve-claude-md
```

Under 10 minutes if prerequisites installed. Under 60 minutes from scratch.

<div align="right">

[![][back-to-top]][readme-top]

</div>

## Skills Reference

| Skill | Description | Example |
|-------|-------------|---------|
| `/revolve-setup` | Interactive wizard — configure vault, check deps | `/revolve-setup` |
| `/yt-search` | Search YouTube via yt-dlp | `/yt-search "Claude Code skills"` |
| `/research-pipeline` | Collect → NotebookLM → Obsidian note | `/research-pipeline youtube "AI agents"` |
| `/evolve-claude-md` | Scan conversations + notes → append to CLAUDE.md | `/evolve-claude-md --days 7` |

<div align="right">

[![][back-to-top]][readme-top]

</div>

## Sync Script

Standalone Python script that converts AI conversations into Obsidian Markdown notes with image extraction.

| Provider | Format | Status |
|----------|--------|--------|
| Claude | `.jsonl` | Full conversations |
| Codex | sessions `.jsonl` | Full conversations |
| OpenCode | `prompt-history.jsonl` | Prompts only |
| Gemini | `session-*.json` | Full conversations |

Supports one-shot sync and automatic sync via launchd.

See [`scripts/README.md`][sync-docs] for setup and usage.

<div align="right">

[![][back-to-top]][readme-top]

</div>

## Templates

Copy from `templates/` to your vault's template folder:

- **`research-note.md`** — Structured note with frontmatter (date, topic, source type, tags)
- **`research-index.md`** — Dataview-powered index across all research notes

<div align="right">

[![][back-to-top]][readme-top]

</div>

## Configuration

Run `/revolve-setup` to generate config automatically, or copy `config.md.example` to `~/.config/revolve/config.md`.

| Field | Required | Description |
|-------|----------|-------------|
| `vault_path` | Yes | Absolute path to your Obsidian vault |
| `output_dir` | Yes | Relative path within vault for research notes |
| `screenshots_dir` | No | Relative path for screenshot attachments |
| `sync_providers` | No | Comma-separated: `claude,codex,opencode,gemini` |

Full schema: [`docs/config-contract.md`][config-contract]

<div align="right">

[![][back-to-top]][readme-top]

</div>

## Works With

| Tool | Status | What it adds |
|------|--------|-------------|
| Standalone | Works | All skills functional without other plugins |
| [Compound Engineering][ce-plugin] | Enhanced | `/ce:plan`, `/ce:work`, `/ce:review`, `/ce:compound` |
| [Forge][forge-repo] | Enhanced | CLAUDE.md workflow methodology templates |

<div align="right">

[![][back-to-top]][readme-top]

</div>

## Contributing

Issues, feature requests, and PRs welcome.

<div align="right">

[![][back-to-top]][readme-top]

</div>

## License

[MIT][license]

<!-- Navigation -->
[readme-top]: #readme-top
[how-it-works]: #how-it-works
[prerequisites]: #prerequisites
[installation]: #installation
[quick-start]: #quick-start
[skills-ref]: #skills-reference
[sync-section]: #sync-script
[templates-section]: #templates
[config-section]: #configuration
[contributing]: #contributing
[license-section]: #license

<!-- Images — 替换为你的实际图片 URL -->
[banner]: images/banner.jpg
[flywheel-diagram]: images/flywheel.jpg
[back-to-top]: https://img.shields.io/badge/-Back_to_top-gray?style=flat-square

<!-- Badges -->
[license-badge]: https://img.shields.io/badge/License-MIT-blue?style=flat-square
[claude-badge]: https://img.shields.io/badge/Claude_Code-Plugin-7C3AED?style=flat-square&logo=data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjQiIGhlaWdodD0iMjQiIHZpZXdCb3g9IjAgMCAyNCAyNCIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj48cGF0aCBkPSJNMTIgMkM2LjQ4IDIgMiA2LjQ4IDIgMTJzNC40OCAxMCAxMCAxMCAxMC00LjQ4IDEwLTEwUzE3LjUyIDIgMTIgMnoiIGZpbGw9IndoaXRlIi8+PC9zdmc+
[plugin-badge]: https://img.shields.io/badge/Install-Plugin-14B8A6?style=flat-square
[lang-en-badge]: https://img.shields.io/badge/English-lightgrey?style=flat-square
[lang-zh-badge]: https://img.shields.io/badge/简体中文-lightgrey?style=flat-square

<!-- Links -->
[license]: LICENSE
[claude-code]: https://claude.ai/code
[obsidian]: https://obsidian.md
[install-url]: https://github.com/eisen0419/revolve
[lang-en]: README.md
[lang-zh]: README_CN.md
[sync-docs]: scripts/README.md
[config-contract]: docs/config-contract.md
[ce-plugin]: https://github.com/EveryInc/compound-engineering-plugin
[forge-repo]: https://github.com/eisen0419/forge
