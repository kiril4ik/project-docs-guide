# Maintenance

> **What:** How to keep docs correct over time: ownership, update triggers, review cycles, automation (linting, link checking, CI), deprecation and archiving.
> **Read when:** setting up a docs process, or when docs keep going stale.

## TL;DR

- **Ownership:** every doc or folder has an owner team. Enforce it with `CODEOWNERS`.
- **Docs change with code:** same PR, with a checkbox in the PR template.
- **Review cycle:** a `last_reviewed` date, and a reminder for anything older than 6–12 months.
- **Automate** what you can: markdownlint, a link checker, spell/style checks, front-matter validation, secret scanning.
- **Deprecate visibly, archive or delete decisively.**

---

## Ownership

```text
# .github/CODEOWNERS
/docs/architecture/          @org/tech-leads
/docs/requirements/billing/  @org/team-billing @org/product-billing
/docs/operations/            @org/platform
/docs/public/                @org/docs-team
/AGENTS.md                   @org/tech-leads
```

The owner doesn't write everything. They make sure it **stays correct** and they review changes.

## Update triggers

| When this happens | Update |
|---|---|
| Public API changes | API spec + guide + CHANGELOG |
| New env var / config | `.env.example` + configuration doc |
| Architectural decision | New ADR (+ overview if the big picture changed) |
| Business rule changes | Rules catalog (new ID or versioned rule) + affected PRDs/tests |
| Incident | Postmortem + runbook improvements |
| Onboarding friction | Getting-started fix by the new person |
| Release | CHANGELOG, release notes |
| Repeated question in chat | FAQ or the relevant doc |

Add this to the PR template:

```markdown
## Docs
- [ ] Docs updated (or not needed because: ___)
```

## Review cycles

| Doc kind | Review |
|---|---|
| Getting started, runbooks | Every 3–6 months, or on every failure |
| Architecture overview, conventions | Every 6 months |
| Reference (generated) | Automatic |
| ADRs, postmortems | Never edited (immutable); status updates only |
| Requirements (shipped) | Archive after ship; rules stay living |

Automate a staleness report: a script that lists files whose `last_reviewed` is older than N months and opens an issue for each owner.

---

## Automation

| Check | Tools (examples) | Catches |
|---|---|---|
| Markdown lint | `markdownlint-cli2`, `remark-lint` | Heading levels, list style, trailing spaces |
| Prose / style lint | **Vale** (custom style rules), `alex` | Banned words ("simply"), terminology, passive voice |
| Spelling | `cspell`, `codespell` | Typos, with project dictionary |
| Link check | `lychee`, `markdown-link-check` | Broken internal and external links, bad anchors |
| Front matter validation | Custom script / JSON Schema | Missing owner, invalid status |
| Orphan check | Custom script | Pages not linked from any index |
| Secret scanning | `gitleaks`, `trufflehog`, platform scanning | Leaked credentials in docs |
| API spec lint | `spectral`, `redocly lint` | Missing descriptions/examples |
| Code samples | Extract-and-run scripts, doctest-style tools | Broken examples |

### Example CI job (GitHub Actions)

```yaml
name: docs
on:
  pull_request:
    paths: ['**/*.md', 'api/**']
jobs:
  docs:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Markdown lint
        uses: DavidAnson/markdownlint-cli2-action@v16
        with:
          globs: '**/*.md'
      - name: Link check
        uses: lycheeverse/lychee-action@v2
        with:
          args: --offline --include-fragments '**/*.md'
```

Pin action versions to what's current when you set this up.

### Example `.markdownlint.jsonc`

```jsonc
{
  "default": true,
  "MD013": false,          // line length: off (no hard wrap)
  "MD033": { "allowed_elements": ["details", "summary", "br"] },
  "MD041": true            // first line must be a top-level heading
}
```

Note: MD041 conflicts with front matter in some setups. Configure `front_matter_title` or disable it if needed.

---

## Deprecation and archiving

| Step | Action |
|---|---|
| 1. Deprecate | `status: deprecated`, banner with replacement link and removal date |
| 2. Redirect | Link old → new; on doc sites, add a redirect |
| 3. Archive | Move to `archive/` (if it has historical value) with an "Archived" banner, excluded from site search |
| 4. Delete | Remove; Git keeps history |

Banner example:

```markdown
> [!WARNING]
> **Deprecated** (2026-10). Use [Deployment v2](deployment.md) instead. This page will be deleted after 2027-01.
```

---

## Metrics (optional)

- Page views and search terms with no results (docs site analytics) show you what's missing.
- Time-to-first-commit for new hires shows onboarding quality.
- Percentage of docs with `last_reviewed` under 12 months shows freshness.
- Repeated questions in support or chat channels show doc gaps.

---

**Related:** [writing-process](writing-process.md) · [navigation-and-metadata](../organizing/navigation-and-metadata.md) · [smells-and-fixes](../organizing/smells-and-fixes.md)
**Up:** [Writing](README.md)
