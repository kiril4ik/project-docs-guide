# AI Agent Docs

> **What:** Docs written specifically for AI coding agents and LLM tools: `AGENTS.md`, `CLAUDE.md`, tool-specific rules files, `llms.txt`, agent skills, and where to keep agent-generated documents.
> **Read when:** your team uses AI coding assistants, or you want LLMs to understand your project or product docs correctly.

## TL;DR

- Put an **`AGENTS.md`** (or the tool's file, such as `CLAUDE.md`) at the repo root. It covers commands, conventions, boundaries and a map of the docs.
- Keep it **short and router-like**. Link to existing docs instead of duplicating them.
- Add **nested agent files** in subfolders for area-specific rules (monorepos).
- Make **human docs agent-friendly** too: explicit, structured, consistent paths. See [writing-for-ai-agents](../writing/writing-for-ai-agents.md).
- Give **agent-generated docs** (plans, reports, scratch notes) their **own folder**, separate from human-curated docs.

---

## Agent instruction files

| File | Read by | Notes |
|---|---|---|
| `AGENTS.md` | 20+ agents: Codex, Amp, Jules, Cursor, Factory, GitHub Copilot, Zed, Warp, opencode, others (some, like Aider and Gemini CLI, need config) | Tool-neutral open format, stewarded under the Linux Foundation. Current list: [agents.md](https://agents.md) |
| `CLAUDE.md` | Claude Code | Supports nested files and `@path` imports. Put `@AGENTS.md` in it to reuse the shared file. |
| `.cursor/rules/*.mdc` | Cursor | Rules with glob scoping |
| `.github/copilot-instructions.md` | GitHub Copilot | Repo-wide. Path-specific rules go in `.github/instructions/**/*.instructions.md` with an `applyTo:` glob. |
| `GEMINI.md` | Gemini CLI | Context file name is configurable (can point at `AGENTS.md`) |
| `.windsurf/rules/` | Windsurf | |

**Avoiding duplication across tools:** keep the content in `AGENTS.md`. Make the tool-specific files a thin pointer (for example `CLAUDE.md` containing `@AGENTS.md`) or a symlink, or generate them from one source.

⚠️ Tool support changes quickly. Check each tool's docs before relying on a file name.

### What to put in AGENTS.md

| Section | Example contents |
|---|---|
| Project summary | 2–3 sentences: what, stack, main folders |
| Commands | Install, run, test, lint, build, exact commands |
| Code conventions | Only the non-obvious ones, or a link to the conventions doc |
| Architecture map | Where things live: "Domain logic in `src/Domain/`, never in controllers" |
| Docs map | "Business rules: `docs/requirements/rules/`. ADRs: `docs/architecture/decisions/`" |
| Boundaries | What not to touch: generated files, migrations already applied, secrets, vendor dirs |
| Workflow rules | "Run tests before claiming done", "Update CHANGELOG under Unreleased" |
| Safety | Destructive operations need confirmation, never commit `.env` |

### Rules for agent files

- ✅ **Short.** Agents load it on every task, so long files waste context and dilute attention. Aim for under 200 lines and link out.
- ✅ **Imperative and specific:** "Use `pnpm`, not `npm`" beats "We prefer modern tooling".
- ✅ **Commands in code blocks**, exactly as they should be run.
- ✅ **Nested files** for subprojects: `apps/web/AGENTS.md` adds rules for that area only.
- ❌ Don't paste the architecture doc into it. **Link** to it.
- ❌ Don't include secrets, tokens or internal URLs you wouldn't commit anyway.

Template: [templates/agents-md-template.md](../templates/agents-md-template.md)

---

## llms.txt

A proposed convention ([llmstxt.org](https://llmstxt.org)) for **published docs sites**: a Markdown file at `/llms.txt` that gives LLMs a curated index of the most important pages. Format: an H1 name, a blockquote summary, then H2 sections that list links with one-line descriptions. An `## Optional` section marks content that can be skipped.

Many sites also publish `/llms-full.txt` with the full text of all pages inline. That's a widely used de facto convention, not part of the original proposal. Adoption by the major AI providers isn't confirmed, so treat both files as a cheap extra, not a guarantee.

```markdown
# Payments API

> Payments API for EU merchants: card payments, refunds, payouts.

## Docs
- [Quick start](https://docs.example.com/quick-start.md): first payment in 5 minutes
- [Authentication](https://docs.example.com/auth.md): API keys and scopes
- [Refunds](https://docs.example.com/refunds.md): full and partial refunds, approval rules

## Optional
- [Changelog](https://docs.example.com/changelog.md)
```

Relevant for **public product or API docs**. For in-repo docs, `AGENTS.md` plus a good docs index does the same job.

---

## Agent skills, commands and rules folders

Many agent tools support reusable instruction packs, such as Claude Code skills in `.claude/skills/<name>/SKILL.md` and slash commands in `.claude/commands/`. Treat them like code:

- One folder per skill/command, with a clear name and description.
- Version them in Git and review them in PRs.
- Keep **project knowledge** (business rules, architecture) in the normal docs and have skills **link** to it. Skills hold **procedures**, not facts.

---

## Where to put agent-generated documents

Agents produce plans, specs, research notes, progress reports and session logs. Mixing these into the human docs folder causes **noise and staleness**.

| Kind | Recommended location | Commit? |
|---|---|---|
| Agent instructions (curated) | `AGENTS.md`, `CLAUDE.md`, `.claude/`, `.cursor/` | ✅ |
| Implementation plans / specs being worked on | `.agents/plans/`, `planning/`, `work/specs/` | ✅ (team-visible) or ❌ (personal) |
| Phase reports / decision logs from agent workflows | `.agent-toolkit/reports/`, `.agents/reports/` | ✅ if they record decisions |
| Scratch notes, research dumps, session logs | `.agents/scratch/` (git-ignored) or system temp | ❌ |
| Final, human-reviewed docs | normal docs root (`docs/`, `handbook/`, …) | ✅ |

Principles:

- ✅ Use a **dedicated, clearly named folder** for agent working documents (`.agents/`, `planning/`, `.ai/`), **not** the human docs root.
- ✅ **Promote** agent output into the docs root only after human review, for example a plan becoming an ADR or a design doc.
- ✅ Add a header to agent-written files: `> Generated by an AI agent on 2026-10-09. Status: draft, not reviewed.`
- ✅ Git-ignore scratch output so it doesn't pollute history.
- ❌ Don't let agents write into `docs/` freely without review. It quickly becomes a junk drawer.

Example layout:

```
repo/
├── AGENTS.md                  curated instructions (committed)
├── CLAUDE.md                  "@AGENTS.md" import + Claude-specific bits
├── .claude/
│   ├── skills/
│   └── commands/
├── .agents/
│   ├── plans/                 active implementation plans (committed)
│   ├── reports/               workflow decision logs (committed)
│   └── scratch/               ignored by .gitignore
└── docs/                      human-curated documentation only
```

---

**Related:** [writing-for-ai-agents](../writing/writing-for-ai-agents.md) · [developer-docs](developer-docs.md) · [navigation-and-metadata](../organizing/navigation-and-metadata.md)
**Up:** [Doc types](README.md)
