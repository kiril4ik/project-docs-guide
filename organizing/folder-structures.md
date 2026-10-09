# Folder Structures: Ready-Made Trees

> **What:** Complete, copyable documentation trees for eight common project shapes, each annotated with the model it uses and why.
> **Read when:** you know roughly what kind of project you have and want a starting structure. To pick the shape, use the [decision guide](../choosing-structure/decision-guide.md).

## TL;DR

- Start with the **smallest tree that fits**, and only create a folder when it has content.
- Every tree has the same core: **root README → docs index → a few topic folders → glossary**.
- `docs/` is used below as the docs root. Rename it if you want ([naming the docs root](naming-conventions.md#naming-the-documentation-root)).

| # | Project shape | Model |
|---|---|---|
| [A](#a-small-project--solo--mvp) | Small project / solo / MVP | Flat |
| [B](#b-web-application-single-team) | Web application, single team | By doc type |
| [C](#c-saas-product-several-teams) | SaaS product, several teams | Hybrid: type → domain |
| [D](#d-monorepo) | Monorepo | Central + co-located |
| [E](#e-open-source-library--sdk) | Open-source library / SDK | Diátaxis + root community files |
| [F](#f-public-api-product) | Public API product | Audience → Diátaxis, versioned |
| [G](#g-enterprise--regulated--client-project) | Enterprise / regulated / client project | Type, formal requirements, traceability |
| [H](#h-ai-agent-heavy-repository) | AI-agent-heavy repository | Any + agent layer |

---

## A. Small project / solo / MVP

**Model:** [flat](models/flat-with-metadata.md). **Why:** few docs, so structure would add friction.

```
project/
├── README.md              what, quick start, links
├── CHANGELOG.md
├── .env.example           documented env vars
└── docs/
    ├── README.md          one-line index
    ├── architecture.md    one page + a Mermaid diagram
    ├── decisions.md       decision log table
    ├── deployment.md
    └── requirements.md    scope, user stories, business rules
```

**Move on** when `docs/` has about 15+ files, or you get a second team member → B.

---

## B. Web application, single team

**Model:** [by doc type](models/by-doc-type.md). **Why:** one team, and readers search by kind of doc.

```
project/
├── README.md
├── CONTRIBUTING.md
├── CHANGELOG.md
├── AGENTS.md                     optional, see H
└── docs/
    ├── README.md                 index + "how these docs are organized"
    ├── getting-started/
    │   ├── README.md             local setup
    │   ├── configuration.md
    │   └── troubleshooting.md
    ├── architecture/
    │   ├── README.md             overview, C4 context + container
    │   ├── data-model.md
    │   └── decisions/
    │       ├── README.md         ADR index
    │       └── 0001-record-architecture-decisions.md
    ├── requirements/
    │   ├── README.md
    │   ├── prd-<feature>.md
    │   ├── business-rules.md
    │   └── non-functional.md
    ├── api/
    │   ├── README.md
    │   └── openapi.yaml
    ├── development/
    │   ├── conventions.md
    │   └── testing.md
    ├── operations/
    │   ├── deployment.md
    │   └── runbooks/
    └── glossary.md
```

---

## C. SaaS product, several teams

**Model:** [hybrid](models/hybrid.md), type → domain. **Why:** type is still how people search, and domains keep folders small and owned.

```
product/
├── README.md
├── CONTRIBUTING.md
├── CHANGELOG.md
├── AGENTS.md
├── .github/CODEOWNERS            docs/requirements/billing/ @team-billing ...
└── docs/
    ├── README.md
    ├── getting-started/
    ├── architecture/
    │   ├── README.md
    │   ├── domains.md            map: domain → team → services
    │   └── decisions/
    ├── requirements/
    │   ├── README.md
    │   ├── billing/
    │   │   ├── README.md
    │   │   ├── rules.md          BR-BIL-xx
    │   │   └── features/
    │   │       ├── partial-refunds.md        status: shipped
    │   │       └── multi-currency.md         status: draft
    │   ├── catalog/
    │   ├── identity/
    │   └── non-functional.md
    ├── api/
    │   ├── README.md
    │   ├── guides/
    │   └── reference/            generated
    ├── operations/
    │   ├── environments.md
    │   ├── deployment.md
    │   ├── runbooks/
    │   │   ├── README.md         index by alert name
    │   │   ├── billing/
    │   │   └── platform/
    │   └── postmortems/
    │       └── 2026-09-18-checkout-outage.md
    ├── rfcs/
    │   └── 0042-multi-currency.md
    ├── archive/
    └── glossary.md
```

---

## D. Monorepo

**Model:** [central + co-located](models/co-located.md). **Why:** module docs stay fresh next to the code, and cross-cutting docs stay central.

```
monorepo/
├── README.md                 map of apps/services/packages
├── CONTRIBUTING.md
├── AGENTS.md                 global agent rules
├── docs/                     cross-cutting only
│   ├── README.md
│   ├── architecture/
│   │   ├── README.md
│   │   └── decisions/        cross-cutting ADRs
│   ├── conventions/
│   ├── requirements/         product-level requirements
│   └── glossary.md
├── apps/
│   └── web/
│       ├── README.md
│       └── AGENTS.md         web-specific agent rules
├── services/
│   └── billing/
│       ├── README.md
│       ├── openapi.yaml
│       └── docs/
│           ├── runbooks/
│           └── decisions/    service-scoped ADRs
└── packages/
    └── ui-kit/
        ├── README.md
        └── src/**/*.mdx      component docs
```

Rule: **one module → in the module; two or more → in `docs/`.**

---

## E. Open-source library / SDK

**Model:** [Diátaxis](models/diataxis.md) for user docs + standard community files. **Why:** the main readers are users of the library, and contributors are secondary.

```
library/
├── README.md                  pitch, install, 30-second example, links
├── CHANGELOG.md
├── CONTRIBUTING.md
├── CODE_OF_CONDUCT.md
├── SECURITY.md
├── LICENSE
├── .github/
│   ├── ISSUE_TEMPLATE/
│   └── PULL_REQUEST_TEMPLATE.md
└── docs/                      published to docs site
    ├── index.md
    ├── tutorials/
    │   └── getting-started.md
    ├── how-to/
    │   ├── configure-retries.md
    │   └── migrate-from-v2.md
    ├── reference/
    │   ├── api/               generated from docstrings
    │   └── configuration.md
    ├── explanation/
    │   └── design-principles.md
    └── contributing/          maintainer docs (architecture, release process)
        ├── architecture.md
        └── releasing.md
```

---

## F. Public API product

**Model:** audience → Diátaxis, with [versioned](models/by-version.md) reference. **Why:** external integrators need a polished portal, and internal docs must not leak.

```
api-product/
├── README.md
├── openapi/
│   ├── v1.yaml
│   └── v2.yaml                    source of truth
├── docs/
│   ├── public/                    ⬅ published developer portal
│   │   ├── index.md
│   │   ├── quick-start.md         tutorial
│   │   ├── authentication.md
│   │   ├── guides/                how-to
│   │   ├── concepts/              explanation: pagination, idempotency, errors, versioning
│   │   ├── reference/
│   │   │   ├── v2/                generated
│   │   │   └── v1/                deprecated banner
│   │   ├── webhooks.md
│   │   ├── sdks.md
│   │   ├── changelog.md
│   │   └── migration-v1-to-v2.md
│   └── internal/                  not published
│       ├── architecture/
│       ├── decisions/
│       ├── runbooks/
│       └── requirements/
└── llms.txt                       optional, served at site root
```

---

## G. Enterprise / regulated / client project

**Model:** by doc type with formal requirements and traceability. **Why:** auditors, clients and sign-offs need IDs, versions and approvals.

```
project/
├── README.md
├── CHANGELOG.md
└── docs/
    ├── README.md
    ├── 00-governance/
    │   ├── document-control.md     versions, approvers, review cycle
    │   └── raci.md
    ├── 01-business/
    │   ├── brd.md                  BR-xx, signed off
    │   └── stakeholders.md
    ├── 02-requirements/
    │   ├── srs.md                  FR-xx / NFR-xx
    │   ├── use-cases/
    │   │   └── UC-07-issue-refund.md
    │   ├── business-rules.md
    │   └── traceability-matrix.md  BR → FR → story → test
    ├── 03-architecture/
    │   ├── architecture.md         (arc42 or similar)
    │   └── decisions/
    ├── 04-security-compliance/
    │   ├── data-flows.md
    │   ├── threat-model.md
    │   └── controls.md
    ├── 05-testing/
    │   ├── test-strategy.md
    │   └── test-plans/
    ├── 06-operations/
    │   ├── deployment.md
    │   ├── runbooks/
    │   └── disaster-recovery.md
    ├── 07-user/
    │   └── user-manual.md
    └── glossary.md
```

Numbered top folders are justified **here**, because these docs follow a formal sequence that contracts and audits refer to. See [naming-conventions](naming-conventions.md#numbering-folders-and-files).

---

## H. AI-agent-heavy repository

**Model:** any of the above + an **agent layer** kept separate from human docs. **Why:** agents need short, explicit entry points, and their working files must not pollute curated docs.

```
project/
├── README.md
├── AGENTS.md                  router: commands, conventions, docs map, boundaries
├── CLAUDE.md                  "@AGENTS.md" import + Claude-specific notes
├── .claude/
│   ├── skills/
│   └── commands/
├── .agents/                   agent working area (not human docs)
│   ├── plans/                 active implementation plans
│   ├── reports/               workflow decisions
│   └── scratch/               git-ignored
├── docs/                      human-curated (structure B, C or D)
│   ├── README.md
│   ├── architecture/
│   ├── requirements/
│   │   └── rules/             stable IDs: easy for agents to cite
│   └── glossary.md
└── src/
    └── billing/
        └── AGENTS.md          area-specific rules
```

Details: [ai-agent-docs](../doc-types/ai-agent-docs.md) · [writing-for-ai-agents](../writing/writing-for-ai-agents.md).

---

**Related:** [organizing overview](README.md) · [scenarios](../choosing-structure/scenarios.md) · [hybrid](models/hybrid.md)
**Up:** [Organizing](README.md)
