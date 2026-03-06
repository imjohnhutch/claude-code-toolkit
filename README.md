# Claude Code Toolkit

A curated directory of extensions, skills, hooks, commands, and tools for **Claude Code** — the stuff that's actually hard to find and useful to set up.

Not another list of MCP servers or Claude.ai features. This is focused on what you can plug into Claude Code to make it better at its job.

---

## Table of Contents

- [Skills](#skills)
- [Slash Commands](#slash-commands)
- [Hooks](#hooks)
- [Agents & Orchestrators](#agents--orchestrators)
- [Utilities & Monitoring](#utilities--monitoring)
- [Security](#security)
- [Project Templates](#project-templates)
- [PM & Product Tools](#pm--product-tools)
- [MCP Servers Worth Setting Up](#mcp-servers-worth-setting-up)
- [Learning & Reference](#learning--reference)

---

## Skills

Skills are folders with a `SKILL.md` that Claude loads on demand — domain knowledge, workflows, and specialized instructions without bloating every session.

| Name | What It Does | Link |
|------|-------------|------|
| **Anthropic Official Skills** | Reference skills from Anthropic covering creative, dev, enterprise, and document workflows | [GitHub](https://github.com/anthropics/skills) |
| **Awesome Claude Skills** | 500+ community skills across security, testing, design, PM, and more | [GitHub](https://github.com/VoltAgent/awesome-agent-skills) |
| **Claude Skills Collection** | 86 production-ready skill packages covering the full delivery workflow — research, planning, implementation, testing, review | [GitHub](https://github.com/levnikolaevich/claude-code-skills) |
| **Awesome Claude Skills (travisvn)** | Curated list focused on quality over quantity, organized by category | [GitHub](https://github.com/travisvn/awesome-claude-skills) |
| **Product Manager Skills** | 46 PM frameworks (RICE, jobs-to-be-done, competitive analysis, etc.) as agent skills | [GitHub](https://github.com/deanpeters/Product-Manager-Skills) |
| **Everything Claude Code** | Performance-optimized skill harness with memory, security, and research-first development patterns | [GitHub](https://github.com/affaan-m/everything-claude-code) |

---

## Slash Commands

Custom `.md` files in `.claude/commands/` that become `/project:command-name` shortcuts. Drop them in your repo and your whole team gets them.

| Name | What It Does | Link |
|------|-------------|------|
| **wshobson/commands** | 57 production-ready commands — 15 multi-agent workflows + 42 single-purpose tools (feature dev, security scan, API scaffold, smart-fix) | [GitHub](https://github.com/wshobson/commands) |
| **steadycursor/steadystart** | Bootstrap commands including `/commit-fast` (auto-picks first suggested commit message) and `/commit` (structured commit flow) | [GitHub](https://github.com/steadycursor/steadystart) |
| **Claude Command Suite** | Structured workflows for code review, feature creation, security auditing, and architectural analysis | [GitHub](https://github.com/qdhenry/Claude-Command-Suite) |
| **Alireza's Claude Skills** | Collection of subagent commands and real-world workflow automations | [GitHub](https://github.com/alirezarezvani/claude-skills) |

**How to install:** Clone or copy the `.md` files into your project's `.claude/commands/` directory.

---

## Hooks

Hooks are deterministic — they run every time, no exceptions. Configure them in `.claude/settings.json` for rules that must never be broken.

| Name | What It Does | Link |
|------|-------------|------|
| **Claude Code Hooks Mastery** | All 13 hook events implemented with examples — security gates, TTS feedback, transcript backups, subagent orchestration. The best learning resource for hooks. | [GitHub](https://github.com/disler/claude-code-hooks-mastery) |
| **Lasso Security Hooks** | Prompt injection defense hooks — scans tool inputs/outputs against 50+ detection patterns, injects warnings into Claude's context | [GitHub](https://github.com/lasso-security/claude-hooks) |
| **cc-tools** | High-performance Go hooks for smart linting, testing, and statusline generation with minimal overhead | Referenced in [awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) |

### Common Hook Recipes

**Auto-format on every edit (Prettier):**
```json
{
  "hooks": {
    "PostToolUse": [{
      "matcher": "Write|Edit",
      "command": "npx prettier --write \"$FILE_PATH\""
    }]
  }
}
```

**Block dangerous shell commands:**
```json
{
  "hooks": {
    "PreToolUse": [{
      "matcher": "Bash",
      "command": "echo $INPUT | grep -qi 'drop table\\|rm -rf /' && exit 2 || exit 0"
    }]
  }
}
```

See the [official hooks guide](https://code.claude.com/docs/en/hooks-guide) for all 14 lifecycle events.

---

## Agents & Orchestrators

Multi-agent setups where Claude Code delegates to specialized sub-agents for complex workflows.

| Name | What It Does | Link |
|------|-------------|------|
| **CCPM** | Full project management system using GitHub Issues + git worktrees for parallel agent execution. Turns PRDs into epics, epics into issues, issues into code. | [GitHub](https://github.com/automazeio/ccpm) |
| **Claude Code PM** | Feature-packed PM workflow with specialized agents, slash commands, and documentation-first approach | Referenced in [awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) |
| **Claude Code Action** | Run Claude Code in GitHub Actions — automated PR reviews, issue triage, code generation on CI triggers | [GitHub](https://github.com/anthropics/claude-code-action) |
| **Claude Code Security Review** | GitHub Action that uses Claude to analyze code changes for security vulnerabilities on every PR | [GitHub](https://github.com/anthropics/claude-code-security-review) |

---

## Utilities & Monitoring

| Name | What It Does | Link |
|------|-------------|------|
| **ccusage** | CLI tool that analyzes your Claude Code JSONL logs — daily/monthly/session token usage and cost breakdowns | [GitHub](https://github.com/ryoppippi/ccusage) |
| **Claude Code Usage Monitor** | Real-time token consumption chart with cost estimates and rate limit predictions | [GitHub](https://github.com/Maciek-roboblog/Claude-Code-Usage-Monitor) |
| **Claude Code Usage Analyzer** | Comprehensive cost & token breakdown by model and token type using LiteLLM pricing data | [GitHub](https://github.com/aarora79/claude-code-usage-analyzer) |
| **cclogviewer** | Renders Claude Code `.jsonl` conversation files as pretty HTML for review | Referenced in [awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) |
| **ccexp** | Interactive CLI for discovering and managing Claude Code config files and slash commands | Referenced in [awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) |

---

## Security

| Name | What It Does | Link |
|------|-------------|------|
| **Lasso Claude Hooks** | Runtime prompt injection detection — scans tool outputs for instruction override, role-playing, encoding attacks, and context manipulation | [GitHub](https://github.com/lasso-security/claude-hooks) |
| **Claude Code Security Review** | GitHub Action for automated security vulnerability scanning on PRs | [GitHub](https://github.com/anthropics/claude-code-security-review) |
| **Parry** | Prompt injection scanner hook (early stage) — scans for injection attacks, secrets, and data exfiltration | Referenced in [awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) |

---

## Project Templates

Full `.claude/` directory setups you can learn from or fork.

| Name | What It Does | Link |
|------|-------------|------|
| **claude-code-showcase** | Complete reference config — hooks, skills, agents, commands, and GitHub Actions workflows. Includes auto skill-matching on every prompt. | [GitHub](https://github.com/ChrisWiles/claude-code-showcase) |
| **steadystart** | Opinionated starter kit with bootstrapping commands, commit workflows, and meta-commands for creating new slash commands | [GitHub](https://github.com/steadycursor/steadystart) |
| **Claude Code Best Practice** | Battle-tested CLAUDE.md patterns and project structure conventions | [GitHub](https://github.com/shanraisshan/claude-code-best-practice) |
| **Everything You Need to Know** | All-in-one guide repo covering setup, commands, hooks, workflows, MCP, and the BMAD method | [GitHub](https://github.com/wesammustafa/Claude-Code-Everything-You-Need-to-Know) |

---

## PM & Product Tools

Extensions specifically useful if you're a product or program manager using Claude Code.

| Name | What It Does | Link |
|------|-------------|------|
| **CCPM** | GitHub Issues-based project management — PRD to epic to issue to code with full traceability | [GitHub](https://github.com/automazeio/ccpm) |
| **Product Manager Skills** | 46 PM frameworks as agent skills — RICE scoring, user story mapping, competitive analysis, stakeholder comms | [GitHub](https://github.com/deanpeters/Product-Manager-Skills) |
| **Claude Code for PMs (course)** | Free hands-on tutorial covering file ops, agents, sub-agents, and PM-specific workflows | [Website](https://ccforpms.com/) |
| **prodmgmt.world** | PM plugins, guides, and workflow templates for Claude Code | [Website](https://www.prodmgmt.world/claude-code) |

---

## MCP Servers Worth Setting Up

Not every MCP server — just the ones that meaningfully extend what Claude Code can do for a developer or PM.

| Server | Why It's Worth It | Link |
|--------|------------------|------|
| **Context7** | Feeds Claude up-to-date library/framework docs so it stops hallucinating API signatures | Community |
| **Playwright** | Real browser testing — Claude can write and run e2e tests, not just unit tests | [GitHub](https://github.com/microsoft/playwright-mcp) |
| **Desktop Commander** | File management + terminal access + diff-based editing in one server — replaces 3 separate MCPs | [Website](https://desktopcommander.app) |
| **GitHub** | PRs, issues, code search, CI status without leaving the terminal | [GitHub](https://github.com/modelcontextprotocol/servers/tree/main/src/github) |
| **Linear** | Manage issues and projects — great for PM workflows | [GitHub](https://github.com/linear/linear-mcp-server) |
| **Notion** | Read/update Notion pages — useful for specs and docs | [GitHub](https://github.com/makenotion/notion-mcp-server) |
| **Sentry** | Query production errors and performance data directly | [GitHub](https://github.com/getsentry/sentry-mcp) |
| **Memory** | Persistent knowledge graph across sessions | [GitHub](https://github.com/modelcontextprotocol/servers/tree/main/src/memory) |
| **PostgreSQL** | Natural language database queries — Claude writes and runs SQL for you | [GitHub](https://github.com/modelcontextprotocol/servers/tree/main/src/postgres) |

---

## Learning & Reference

| Resource | What It Covers | Link |
|----------|---------------|------|
| **Claude Code Docs** | Official docs — skills, hooks, commands, MCP, settings | [Docs](https://code.claude.com/docs/en) |
| **Awesome Claude Code** | The most comprehensive community list — updated frequently | [GitHub](https://github.com/hesreallyhim/awesome-claude-code) |
| **Agent Skills Spec** | The open standard for how skills work across agents | [GitHub](https://github.com/anthropics/skills/blob/main/spec/agent-skills-spec.md) |
| **Hooks Complete Guide** | 20+ ready-to-use hook examples with explanations | [Dev.to](https://dev.to/lukaszfryc/claude-code-hooks-complete-guide-with-20-ready-to-use-examples-2026-dcg) |
| **Writing a Good CLAUDE.md** | Best practices — keep it under 200 lines, use @imports, prefer pointers over copies | [HumanLayer](https://www.humanlayer.dev/blog/writing-a-good-claude-md) |
| **Anthropic Cookbook** | Code examples and patterns for the Claude API | [GitHub](https://github.com/anthropics/anthropic-cookbook) |
| **SkillsMP Marketplace** | Browse and install community skills | [Website](https://skillsmp.com) |
| **MCP Hub** | Discover MCP servers | [Website](https://mcphub.io) |

---

## Contributing

Found something useful that's missing? PRs welcome.

1. Fork this repo
2. Add the tool to the right section with a working link and one-line description
3. Submit a PR

Keep it focused on Claude Code extensions — not general AI tools or Claude.ai features.

---

**Maintained by [John Hutchison](https://github.com/imjohnhutch)** — Product & Program Manager.

*Last updated: March 2026*
