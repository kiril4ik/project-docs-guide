# Scenarios: Recommended Setups

> **What:** Recommended documentation setups for common project types: which docs to write first, which model to use, and where to store each doc type.
> **Read when:** you recognize your project in one of the scenarios and want a proven starting point.

## TL;DR

| # | Scenario | Model | Tree |
|---|---|---|---|
| 1 | Solo developer / prototype | Flat | [A](../organizing/folder-structures.md#a-small-project--solo--mvp) |
| 2 | Startup, one product team | By doc type | [B](../organizing/folder-structures.md#b-web-application-single-team) |
| 3 | Scale-up, several product teams | Type → domain | [C](../organizing/folder-structures.md#c-saas-product-several-teams) |
| 4 | Monorepo platform | Central + co-located | [D](../organizing/folder-structures.md#d-monorepo) |
| 5 | Microservices in many repos | Per-service + handbook/portal | [per-service-repo](../organizing/models/per-service-repo.md) |
| 6 | Open-source library | Diátaxis + community files | [E](../organizing/folder-structures.md#e-open-source-library--sdk) |
| 7 | Public API / developer platform | Public/internal → Diátaxis, versioned | [F](../organizing/folder-structures.md#f-public-api-product) |
| 8 | Agency / client project | Type + formal requirements | [G](../organizing/folder-structures.md#g-enterprise--regulated--client-project) (lighter) |
| 9 | Enterprise / regulated | Type + IDs + traceability + document control | [G](../organizing/folder-structures.md#g-enterprise--regulated--client-project) |
| 10 | AI-agent-driven development | Any + agent layer | [H](../organizing/folder-structures.md#h-ai-agent-heavy-repository) |

---

## 1. Solo developer / prototype

- **Write first:** README (what + how to run), `.env.example`, a short decision log.
- **Skip for now:** PRDs, runbooks, CONTRIBUTING.
- **Model:** flat `docs/` with <10 files.
- **Watch for:** "I'll remember why I did that". You won't. Keep the decision log.

## 2. Startup, one product team

- **Write first:** README, getting started, architecture overview (1 page + diagram), ADRs, lightweight PRDs per feature, glossary, deployment.
- **Model:** [by doc type](../organizing/models/by-doc-type.md).
- **Storage:** everything in the repo; user stories in the tracker.
- **Watch for:** PRDs piling up. Mark them `shipped` and move business rules into a living rules doc.

## 3. Scale-up, several product teams

- **Write first:** everything from #2, plus a domain map (domain → team → services), `CODEOWNERS` for docs, a business rules catalog per domain, runbooks per domain, and RFCs for cross-team changes.
- **Model:** [hybrid type → domain](../organizing/models/hybrid.md#1-type--domain-most-common-for-product-teams).
- **Watch for:** each team inventing its own layout. Publish domain-folder templates.

## 4. Monorepo platform

- **Write first:** root README with a package map, module README template, central architecture + conventions, nested `AGENTS.md` per app.
- **Model:** [central + co-located](../organizing/models/co-located.md).
- **Tooling:** a CI check that each package has a README; optional aggregated docs site.
- **Watch for:** central docs duplicating module READMEs. Apply the "one module vs many" rule.

## 5. Microservices in many repos

- **Write first:** repo template with a standard docs layout, handbook repo (landscape, standards, onboarding, glossary), service catalog.
- **Model:** [per-service repos + portal](../organizing/models/per-service-repo.md).
- **Watch for:** cross-service flows documented nowhere. Put sequence diagrams of key flows in the handbook.

## 6. Open-source library

- **Write first:** README with a 30-second example, getting-started tutorial, API reference (generated), CHANGELOG, CONTRIBUTING, SECURITY, LICENSE, CODE_OF_CONDUCT.
- **Model:** [Diátaxis](../organizing/models/diataxis.md); maintainer docs in a separate `contributing/` section.
- **Publishing:** docs site with versioning once there are multiple major versions in use.
- **Watch for:** README trying to be the whole manual.

## 7. Public API / developer platform

- **Write first:** quick start (first call in 5 minutes), authentication, error catalog, generated reference, webhooks, changelog, versioning policy.
- **Model:** public/internal split; public is Diátaxis; reference [versioned](../organizing/models/by-version.md).
- **Extras:** `llms.txt`, SDK examples, Postman/Bruno collection, status page link.
- **Watch for:** internal hostnames in examples. Apply the [internal-vs-public](../organizing/internal-vs-public.md) safeguards.

## 8. Agency / client project

- **Write first:** BRD or signed scope, PRD/SRS with requirement IDs, change request log, handover docs (deployment, admin guide, runbooks), user manual.
- **Model:** by doc type with formal requirements; optionally numbered top folders for the deliverable set.
- **Storage:** repo as source; export to PDF for sign-off (with version + approval table).
- **Watch for:** requirement changes agreed in email and never documented. Keep a `requirements/change-log.md`.

## 9. Enterprise / regulated

- **Write first:** document control (versions, approvals, review cycle), BRD, SRS with IDs, traceability matrix, security/compliance docs (data flows, threat model, controls), test strategy, DR plan.
- **Model:** [structure G](../organizing/folder-structures.md#g-enterprise--regulated--client-project).
- **Tooling:** front-matter validation, required reviewers via CODEOWNERS, generated traceability.
- **Watch for:** docs written for auditors that engineers never read. Keep engineer-facing docs (setup, conventions) separate and lean.

## 10. AI-agent-driven development

- **Write first:** `AGENTS.md` (commands, boundaries, docs map), glossary, business rules with stable IDs, architecture overview, conventions with ✅/❌ examples.
- **Model:** any of the above plus a separate agent working area (`.agents/` or similar).
- **Practices:** specs/plans written before implementation; reviewed plans promoted to ADRs/design docs; agent output marked as such.
- **Watch for:** agents writing straight into `docs/` and creating noise. Review before promoting. See [ai-agent-docs](../doc-types/ai-agent-docs.md).

---

**Related:** [decision-guide](decision-guide.md) · [folder-structures](../organizing/folder-structures.md) · [evolving-structure](evolving-structure.md)
**Up:** [Choosing a structure](README.md)
