# Process & Team Docs

> **What:** Docs about how the team works: onboarding, team handbook, roadmap, meeting notes, decision logs, and community/governance files (SECURITY, CODE_OF_CONDUCT, LICENSE, CODEOWNERS).
> **Read when:** the team grows past a few people, the project goes open source, or decisions keep getting lost.

## TL;DR

- **Onboarding** is a checklist plus links. It doesn't duplicate other docs.
- Keep **decisions** in a searchable log. Meeting notes alone aren't enough.
- Standard **community files** have fixed names and locations, and GitHub/GitLab recognize them.
- Team/process docs often fit a **wiki or handbook repo** better than the product repo.

---

## Process doc set

| Doc | Purpose | Usual location |
|---|---|---|
| Onboarding guide | New member's first days/weeks | `onboarding/` or team handbook |
| Team handbook | Working agreements, rituals, roles, tools | separate `handbook` repo or wiki |
| Roadmap | Planned direction and priorities | wiki / product tool / `product/roadmap.md` |
| Meeting notes | Record of discussions | wiki or `meetings/YYYY-MM-DD-topic.md` |
| Decision log | Non-architectural decisions (process, product, org) | `decisions.md` or `decisions/` |
| Definition of Done / Ready | Shared quality bar | CONTRIBUTING or handbook |
| Release process | Who releases, how, when | operations docs |
| Glossary | Shared vocabulary | `<docs-root>/glossary.md` |

## Standard repository files

These have **conventional names and locations**. Platforms detect them and link them in the UI.

| File | Purpose | Location |
|---|---|---|
| `README.md` | Front door | root |
| `LICENSE` | Legal terms | root |
| `CONTRIBUTING.md` | Contribution guide | root, `.github/` or `docs/` |
| `CODE_OF_CONDUCT.md` | Community behavior rules | root or `.github/` |
| `SECURITY.md` | How to report vulnerabilities, supported versions | root or `.github/` |
| `SUPPORT.md` | Where to get help | root or `.github/` |
| `CHANGELOG.md` | Version history | root |
| `CODEOWNERS` | Who reviews which paths (works for docs ownership too) | `.github/` or root |
| `GOVERNANCE.md` / `MAINTAINERS.md` | Decision-making, maintainers (OSS) | root |
| `.github/PULL_REQUEST_TEMPLATE.md` | PR description template | `.github/` |
| `.github/ISSUE_TEMPLATE/` | Issue forms | `.github/` |

✅ Keep **UPPERCASE** names for these. That convention makes them stand out and lets tools find them.

## Onboarding guide

Structure as a **time-boxed checklist**:

```markdown
# Onboarding

## Day 1
- [ ] Get access: GitHub org, Slack #team-payments, Vault (ask @lead)
- [ ] Run the project locally: [Getting started](../getting-started/README.md)
- [ ] Read: [Architecture overview](../architecture/README.md) (30 min)

## Week 1
- [ ] Read the [glossary](../glossary.md) and [top 10 ADRs](../architecture/decisions/README.md)
- [ ] Ship a small fix (label `good-first-issue`)
- [ ] Shadow an on-call shift

## Who to ask
| Topic | Person/channel |
|---|---|
| Payments domain | @anna, #payments |
```

## Decision log (non-architectural)

ADRs cover technical decisions. Other decisions (process, product scope, tooling) also get lost. A lightweight log works:

```markdown
| Date | Decision | Context / link | Decided by |
|---|---|---|---|
| 2026-09-02 | Move standup to async in Slack | [notes](meetings/2026-09-02-retro.md) | team |
| 2026-08-20 | Drop IE11 support | [PRD-14](../product/prd-14.md) | product + eng |
```

## Meeting notes

- Name them `YYYY-MM-DD-topic.md` so they sort chronologically.
- Always include a **Decisions** section and an **Action items** section (owner + due date).
- Copy decisions into the decision log, because nobody re-reads old meeting notes.

---

**Related:** [developer-docs](developer-docs.md) · [sequential-and-dated model](../organizing/models/sequential-and-dated.md) · [storage-locations](../organizing/storage-locations.md)
**Up:** [Doc types](README.md)
