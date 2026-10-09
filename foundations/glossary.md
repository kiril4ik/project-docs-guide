# Glossary

> **What:** Definitions of the terms used throughout this guide, in alphabetical order.
> **Read when:** you meet an unfamiliar acronym or term.

| Term | Definition | More |
|---|---|---|
| **Acceptance criteria (AC)** | Testable conditions a feature must meet to be accepted. Often written as Given/When/Then. | [business-requirements](../doc-types/business-requirements.md#acceptance-criteria) |
| **ADR** (Architecture Decision Record) | A short, numbered, immutable record of one significant technical decision: its context, the decision and its consequences. | [architecture-docs](../doc-types/architecture-docs.md#architecture-decision-records-adrs) |
| **AGENTS.md** | An open-convention Markdown file at the repo root that gives AI coding agents project instructions. `CLAUDE.md` is the Claude Code equivalent. | [ai-agent-docs](../doc-types/ai-agent-docs.md) |
| **API reference** | Exhaustive, structured description of every endpoint, field, type and error. Ideally generated from a spec. | [api-docs](../doc-types/api-docs.md) |
| **AsyncAPI** | Specification format for event-driven/message APIs (Kafka, AMQP, WebSockets). | [api-docs](../doc-types/api-docs.md#event-driven-apis) |
| **BRD** (Business Requirements Document) | Describes the business need, goals, stakeholders, scope and high-level requirements. Answers *why* and *what for the business*. | [business-requirements](../doc-types/business-requirements.md#brd-business-requirements-document) |
| **Business rule** | A statement that defines or constrains some aspect of the business, such as "Refunds over €500 need manager approval". | [business-requirements](../doc-types/business-requirements.md#business-rules-catalog) |
| **C4 model** | A way to diagram software architecture at four zoom levels: Context, Containers, Components, Code. | [architecture-docs](../doc-types/architecture-docs.md#c4-model) |
| **CHANGELOG** | A human-readable, version-by-version list of notable changes. | [developer-docs](../doc-types/developer-docs.md#changelogmd) |
| **Co-located docs** | Docs stored next to the code they describe, such as `src/billing/README.md`. | [organizing-models](../organizing/models/co-located.md) |
| **Design doc / RFC** | A proposal describing how to build something before building it, circulated for feedback. | [architecture-docs](../doc-types/architecture-docs.md#rfcs-and-design-docs) |
| **Diátaxis** | A documentation framework that splits content into four types: tutorials, how-to guides, reference and explanation. | [organizing-models](../organizing/models/diataxis.md) |
| **Docs-as-code** | Treating docs like code: plain text, in Git, reviewed in PRs, tested in CI, published automatically. | [principles](principles.md#3-docs-as-code) |
| **Docs root** | The top-level folder holding project docs (`docs/`, `handbook/`, etc.). | [naming-conventions](../organizing/naming-conventions.md#naming-the-documentation-root) |
| **Front matter** | A YAML metadata block at the top of a Markdown file. | [markdown-essentials](markdown-essentials.md#front-matter-metadata) |
| **FRS / SRS** | Functional / Software Requirements Specification: detailed, often formal, list of what the system must do. | [business-requirements](../doc-types/business-requirements.md#srs--frs-software--functional-requirements-specification) |
| **GFM** | GitHub-Flavored Markdown: CommonMark plus tables, task lists, strikethrough, autolinks, alerts. | [markdown-essentials](markdown-essentials.md#github-flavored-markdown-gfm-extras) |
| **How-to guide** | Goal-oriented steps to solve one specific problem, for a reader who already knows the basics. | [page-patterns](../writing/page-patterns.md#how-to-guide) |
| **llms.txt** | A proposed convention: a Markdown file at a site root that lists and summarizes key docs for LLMs. | [ai-agent-docs](../doc-types/ai-agent-docs.md#llmstxt) |
| **Mermaid** | A text-based diagram syntax rendered by GitHub, GitLab and most doc tools. | [diagrams-and-visuals](../writing/diagrams-and-visuals.md) |
| **NFR** (Non-functional requirement) | A quality attribute: performance, security, availability, accessibility, etc. | [business-requirements](../doc-types/business-requirements.md#non-functional-requirements-nfrs) |
| **OpenAPI** | Machine-readable specification format for HTTP/REST APIs (formerly Swagger). | [api-docs](../doc-types/api-docs.md#spec-first-openapi) |
| **Postmortem** | A blameless write-up of an incident: timeline, impact, root cause, action items. | [operations-docs](../doc-types/operations-docs.md#incident-postmortems) |
| **PRD** (Product Requirements Document) | Describes a product or feature: problem, users, scope, requirements, success metrics. | [business-requirements](../doc-types/business-requirements.md#prd-product-requirements-document) |
| **Reference doc** | Accurate, complete, structured facts (APIs, config options, CLI flags), meant to be looked up rather than read through. | [page-patterns](../writing/page-patterns.md#reference-page) |
| **Runbook** | Step-by-step operational procedure for a specific situation or alert. | [operations-docs](../doc-types/operations-docs.md#runbooks) |
| **SSOT** (Single source of truth) | Each fact is maintained in exactly one place, and everything else links to it. | [principles](principles.md#2-single-source-of-truth-ssot) |
| **Tutorial** | Learning-oriented lesson that takes a beginner through a complete, guaranteed-to-work exercise. | [page-patterns](../writing/page-patterns.md#tutorial) |
| **Use case** | A structured description of how an actor interacts with the system to reach a goal, including alternative flows. | [business-requirements](../doc-types/business-requirements.md#use-cases) |
| **User story** | A short requirement in the format "As a [role], I want [capability], so that [benefit]". | [business-requirements](../doc-types/business-requirements.md#user-stories) |

---

**Up:** [Foundations](README.md)
