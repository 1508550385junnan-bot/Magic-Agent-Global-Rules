# Agent Global Collaboration Rules

> Version: v2.5 | Updated: 2026-05-26
> Scope: All AI agent interactions (not limited to a single project)

---

## Core Principle

**Don't make decisions for me. Don't omit content. Don't give me summaries as deliverables. Give me complete, directly executable, full content.**

---

## Language

This repository provides bilingual rules:
- **`CLAUDE.md`** — Full Chinese version (optimized for DeepSeek, the author's daily driver)
- **`AGENTS.md`** — Full English version (for Claude, GPT, Gemini, and other English-optimized models)
- **`skills/global-collaboration-rules/SKILL.md`** — Installable skill (English, under 200 lines, core rules only)

Pick the file that matches your model:
| Model | Recommended File | Install As |
|-------|-----------------|------------|
| DeepSeek | `CLAUDE.md` | Copy to project root as `CLAUDE.md` |
| Claude | `AGENTS.md` | Copy to project root as `CLAUDE.md` |
| GPT / Gemini | `AGENTS.md` | Copy to project root as `AGENTS.md` |
| Any model (skill mode) | `skills/global-collaboration-rules/` | Install via `npx skills add` or copy to `~/.hermes/skills/` |

## Quick Install

### As CLAUDE.md (recommended for most users)
```bash
# Chinese (DeepSeek users)
curl -o CLAUDE.md https://raw.githubusercontent.com/1508550385junnan-bot/agent-global-rules/main/CLAUDE.md

# English (Claude/GPT/Gemini users)
curl -o CLAUDE.md https://raw.githubusercontent.com/1508550385junnan-bot/agent-global-rules/main/AGENTS.md
```

### As a Skill
```bash
npx skills add 1508550385junnan-bot/agent-global-rules@global-collaboration-rules
```

Or manually:
```bash
mkdir -p ~/.hermes/skills/global-collaboration-rules
cp skills/global-collaboration-rules/SKILL.md ~/.hermes/skills/global-collaboration-rules/
```

## What's Inside

| Section | Topic | Key Feature |
|---------|-------|-------------|
| I | How I use agents | Execution flow: goal → plan → confirm → execute → verify |
| II | Output standards | Completeness, self-check checklists, document structure |
| III | Style preferences | Direct, practical, precise, honest |
| IV | Lessons learned | Common agent mistakes + fixes |
| V | Task execution framework | 5-step flow: understand → decompose → plan → execute → deliver |
| VI | Scenario-specific rules | Code gen, docs, workflows, data, debugging |
| VII | Absolute prohibitions | 12 rules: no omission, no fake execution, no scope creep... |
| VIII | Quick reference card | ASCII cheat sheet |
| IX | Context preservation | Requirements freeze, anti-drift checks, 3-strike protocol |
| X | Skill borrowing + image fallback + compression | Search skills first, Pillow/OCR for images, 85% auto-compress |
| XI | Token optimization | 4-battlefield framework: input caching, tool sandboxing, output trimming, JIT skills |
| XII | Chinese language rules | Full-pipeline Chinese: thinking, output, comments, commit messages |
| XIII | Code comments, execution boundaries, prompt parsing | No comments in code (thinking suffices), comma=sub-req, period=module |

## Token Savings (Expected)

| Optimization | Method | Savings |
|-------------|--------|---------|
| Input caching | Static system prompt + append-only messages | 90% on cache hit |
| Tool output sandboxing | Raw output to files, summary only in context | 98% (56KB → 1.2KB) |
| Think-in-Code | Write scripts instead of reading 50 files | 195x (700KB → 3.6KB) |
| Output trimming | No filler, no pleasantries | 20-75% |
| Code comments skip | Thinking process explains logic | ~10-20% |
| JIT skill loading | Don't load unused skills | Variable |

## Author

**大虎子 (Da Hu Zi)** — developer of [AI Tools One-Click Download](https://github.com/1508550385junnan-bot/ai-tools-one-click-download)

## License

MIT
