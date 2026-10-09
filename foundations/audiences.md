# Documentation Audiences

> **What:** The reader groups a project has, what each one needs, and how each one looks for information.
> **Read when:** deciding what to write, or when choosing to organize docs [by audience](../organizing/models/by-audience.md).

## TL;DR

- Most projects have 4–7 distinct audiences. List yours **before** designing a structure.
- Audiences differ in **goal**, **vocabulary**, **depth** and **how they search**.
- An audience with very different needs (for example external API consumers or end users) usually deserves its **own section, or even its own site**.
- AI agents are now a real audience. They need explicit, structured and unambiguous docs.

---

## Audience map

| Audience | Main goal | Wants | Doesn't want | Typical docs |
|---|---|---|---|---|
| **New developer** (onboarding) | Get productive fast | Setup steps, architecture overview, "where is X" | Deep history, every edge case | README, getting-started, architecture overview, glossary |
| **Maintainer / core developer** | Change code safely | Conventions, decisions and their reasons, internals | Marketing, basics | ADRs, design docs, coding conventions, CONTRIBUTING |
| **API consumer** (internal or external) | Integrate quickly | Auth, endpoints, examples, errors, limits | Internal implementation | API reference, quick start, SDK guides, changelog |
| **Product / business** | Define and verify behavior | Requirements, business rules, scope, status | Code-level detail | BRD, PRD, user stories, business rules, roadmap |
| **QA / testers** | Verify behavior | Acceptance criteria, rules, edge cases, test data | Architecture internals | User stories + acceptance criteria, test plans |
| **Operations / SRE / on-call** | Keep it running, fix it fast at 3 a.m. | Runbooks, dashboards, alerts, rollback steps | Long explanations | Runbooks, deployment guides, postmortems, SLOs |
| **End user / customer** | Get their task done | Task-focused guides, screenshots, FAQ | Technical jargon | User guides, tutorials, FAQ, release notes |
| **Security / compliance / auditor** | Check controls and evidence | Data flows, policies, access, decisions | Opinions without evidence | SECURITY.md, data-flow diagrams, policies, ADRs |
| **AI coding agent** | Act correctly in the repo | Commands, conventions, boundaries, file map | Ambiguity, implied knowledge | AGENTS.md / CLAUDE.md, rules files, structured docs |

## How each audience searches

This decides how you organize and name things.

| Audience | Typical search behavior | Implication |
|---|---|---|
| New developer | Linear: reads from the top | Give a clear *reading path* in README |
| Maintainer | Targeted: "why did we choose Kafka?" | Searchable decision log (ADRs), good file names |
| API consumer | By endpoint or task: "create invoice" | Reference organized by resource, plus task guides |
| Business | By feature or domain: "refund rules" | Requirements organized by domain/feature |
| On-call | Under stress, by symptom: "500s on checkout" | Runbooks named after **symptoms/alerts**, not systems |
| End user | Search box and FAQ | Task-named pages, synonyms in text |
| AI agent | Reads entry files, follows links, uses grep/search | Predictable paths, explicit index files, consistent headings |

## Write an audience list for your project

Add this short table to your docs index (for example `docs/README.md`). It forces clarity and helps contributors put new docs in the right place:

```markdown
## Who these docs are for

| Audience | Start here |
|---|---|
| New developers | [Getting started](getting-started/README.md) |
| API consumers | [API docs](api/README.md) |
| Product & business | [Requirements](requirements/README.md) |
| On-call | [Runbooks](operations/runbooks/README.md) |
```

## Internal vs external audiences

| | Internal | External |
|---|---|---|
| Tone | Direct, can use team jargon (defined in glossary) | Polished, no internal jargon |
| Security | Can mention internal hosts and tools | Never expose internal URLs, secrets or infrastructure |
| Location | Repo, internal wiki | Public docs site, developer portal |
| Review | Peer review | Peer + editorial (+ legal/security if needed) |

⚠️ **Never mix internal and external docs in the same published output.** Keep them in separate folders (`internal/` vs `public/`) or separate repos, and publish only the public one.

---

**Related:** [principles](principles.md) · [doc types catalog](../doc-types/README.md) · [organizing by audience](../organizing/models/by-audience.md)
**Up:** [Foundations](README.md)
