# Developer Docs

> **What:** Docs for people who work *on* the codebase: README, CONTRIBUTING, getting started, conventions, CHANGELOG, module READMEs.
> **Read when:** setting up a repo's docs, onboarding developers, or deciding what goes in the README versus elsewhere.

## TL;DR

- The **root README** is the front door. It covers what the project is, how to run it and where everything else is. Keep it short and link out.
- **CONTRIBUTING** explains *how to work here*: setup, branching, tests, PR rules.
- **Getting started** should get a new developer from clone to running in **under 30 minutes**.
- Document **why** and **how to use** in docs, and **what this line does** in code comments, and only when that isn't obvious.
- Put a **module README** in every significant package or service in a monorepo.

---

## The developer doc set

| Doc | Required? | Location | Length |
|---|---|---|---|
| `README.md` | Always | repo root | 1–3 screens |
| `CONTRIBUTING.md` | >1 contributor | repo root or `.github/` | 1–4 screens |
| `CHANGELOG.md` | Versioned software | repo root | grows |
| Getting started / local setup | Setup has >3 steps | `<docs-root>/getting-started/` | as needed |
| Coding conventions | >2 developers | `<docs-root>/development/conventions.md` or CONTRIBUTING | 1–5 screens |
| Testing guide | Non-trivial test setup | `<docs-root>/development/testing.md` | |
| Module / package README | Monorepo, libraries | `packages/<name>/README.md` | 1–2 screens |
| Troubleshooting (dev) | Recurring setup problems | `<docs-root>/getting-started/troubleshooting.md` | |
| `.env.example` | Uses env vars | repo root | one line per var, commented |

`<docs-root>` is your docs folder (`docs/`, `handbook/`, …). See [naming the docs root](../organizing/naming-conventions.md#naming-the-documentation-root).

---

## Root README.md

The most-read file in the project. It answers in this order: **What is this? Can I use it? How do I start? Where do I go next?**

### Recommended sections

| # | Section | Contents | Required |
|---|---|---|---|
| 1 | Title + one-line description | What it is in one sentence | ✅ |
| 2 | Badges (optional) | Build, coverage, version, license | |
| 3 | Overview | 2–5 sentences or bullets: problem, solution, key features | ✅ |
| 4 | Quick start | Minimum commands to run it | ✅ |
| 5 | Requirements / prerequisites | Runtime versions, tools, accounts | ✅ |
| 6 | Usage | 1–3 core examples | Libraries/CLIs |
| 7 | Project structure | Short tree of top-level folders | Apps |
| 8 | Documentation | Links to the docs index and main sections | ✅ |
| 9 | Contributing | Link to CONTRIBUTING | |
| 10 | License | Name + link | Public repos |

### README rules

- ✅ Keep it under about 3 screens, and **link out** for details.
- ✅ The quick start must actually work on a clean machine. Test it.
- ✅ Include a "Documentation" section that links to the docs index.
- ❌ Don't paste the whole API reference, architecture or changelog into it.
- ❌ Don't let it become a FAQ dump. Move that to troubleshooting.

Template: [templates/readme-template.md](../templates/readme-template.md)

---

## CONTRIBUTING.md

Answers "**how do I make a change here correctly?**"

| Section | Contents |
|---|---|
| Development setup | Link to getting-started, or inline steps if short |
| Branching & commits | Branch naming, commit format (such as Conventional Commits) |
| Code style | Formatter/linter commands; link to conventions doc |
| Testing | How to run tests, coverage expectations |
| Pull requests | Size, description template, review rules, CI checks |
| Documentation | **Which docs to update with which changes** (see below) |
| Release process | Or link to operations docs |

Include a "docs with code" rule:

```markdown
## Documentation changes

Update docs in the same PR when you:
- add or change a public API endpoint → `docs/api/`
- add an env variable → `.env.example` + `docs/getting-started/configuration.md`
- make an architectural decision → new ADR in `docs/architecture/decisions/`
- change user-visible behavior → `CHANGELOG.md` under "Unreleased"
```

Template: [templates/contributing-template.md](../templates/contributing-template.md)

---

## Getting started / local setup

**Goal:** a new developer runs the project locally in under 30 minutes without asking anyone.

Structure:

1. **Prerequisites**, with exact versions (`Node 22.x`, `PHP 8.3`, `Docker 27+`).
2. **Clone & install**, as copy-pasteable commands.
3. **Configure**: `.env` setup, secrets (where to get them, never the values).
4. **Run**: start command and expected output.
5. **Verify**: "Open http://localhost:3000. You should see…"
6. **Next steps**: links to architecture overview, conventions, first good issues.
7. **Troubleshooting**: the 3–5 most common errors and their fixes.

⚠️ Re-test it every time onboarding fails, and ask every new hire to fix what was wrong. That keeps it current.

---

## Coding conventions

Write down only what tools **can't** enforce. Let formatters and linters handle the rest and just link to their configs.

| Document | Don't document |
|---|---|
| Architecture patterns ("services never call repositories of another module") | Indentation, quotes, semicolons (formatter) |
| Naming of domain concepts | Rules a linter already fails on |
| Error-handling approach | Generic language best practices |
| Where new code of each kind goes | |
| Do/don't examples from *this* codebase | |

Format each rule as **Rule → Why → Example (✅/❌)**:

````markdown
### Money is always stored in minor units

**Why:** floating-point rounding errors in totals.

```php
// ✅
$order->totalCents = 1999;
// ❌
$order->total = 19.99;
```
````

---

## Module / package README

In monorepos and multi-package libraries, each significant unit gets its own README:

```markdown
# payments-service

Handles card payments and refunds via Stripe.

- **Owner:** team-payments
- **Depends on:** orders-service, PostgreSQL, Stripe API
- **Used by:** checkout-web, admin-panel

## Run locally
## Configuration
## Key concepts
## Related docs
- [Refund business rules](../../docs/requirements/payments/refund-rules.md)
- [ADR-0012: Use Stripe](../../docs/architecture/decisions/0012-use-stripe.md)
```

See [co-located model](../organizing/models/co-located.md).

---

## CHANGELOG.md

A curated, human-readable list of notable changes per version. It is **not** a git log dump.

The **Keep a Changelog** format is widely used:

```markdown
# Changelog

All notable changes to this project are documented here.
Format: [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
versioning: [SemVer](https://semver.org/).

## [Unreleased]
### Added
- Refund endpoint `POST /v2/refunds`.

## [2.3.0] - 2026-09-30
### Changed
- Invoices now include tax breakdown.
### Fixed
- Duplicate emails on password reset (#482).
### Deprecated
- `GET /v1/invoices` (removal planned for 3.0.0).
```

Categories: `Added`, `Changed`, `Deprecated`, `Removed`, `Fixed`, `Security`.

| CHANGELOG | Release notes |
|---|---|
| Developers, integrators | End users, customers |
| Complete, technical | Selected highlights, benefit-focused |
| In repo | Docs site, email, in-app |

Can be generated from Conventional Commits (tools: `release-please`, `semantic-release`, `changesets`), but **always review it** before release.

Template: [templates/changelog-template.md](../templates/changelog-template.md)

---

## Code comments vs docs

| Put it in... | When it explains... |
|---|---|
| **Code comment** | *Why* this non-obvious line exists, workarounds, gotchas |
| **Docstring / PHPDoc / JSDoc / TSDoc** | Public function/class contract: params, return, throws, example |
| **Module README** | What this module is for, how to use it, how it fits in |
| **Docs folder** | Cross-cutting topics: architecture, setup, processes, rules |
| **ADR** | Why a significant decision was made |

Rule of thumb: if the explanation becomes wrong when **this file** changes, put it in a comment. If it becomes wrong when **the design** changes, put it in docs.

---

**Related:** [api-docs](api-docs.md) · [architecture-docs](architecture-docs.md) · [ai-agent-docs](ai-agent-docs.md)
**Up:** [Doc types](README.md)
