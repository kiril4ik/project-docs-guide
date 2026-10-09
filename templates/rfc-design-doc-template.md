---
id: RFC-<NNNN>
title: <Title>
status: draft               # draft | review | accepted | rejected | withdrawn | implemented
author: <name>
reviewers: [<name>, <name>]
created: <YYYY-MM-DD>
updated: <YYYY-MM-DD>
decision_date:
related: [<PRD link>, <ADR links>]
---

<!-- TEMPLATE: RFC / design doc. Copy to rfcs/NNNN-short-title.md (or architecture/design/). Write it BEFORE implementing. Typical length 3–15 pages. Delete this comment. -->

# RFC-<NNNN>: <Title>

> **Status:** 🟡 Draft. Comments welcome until <YYYY-MM-DD>.

## Summary

<One paragraph: what you propose and why.>

## Context and problem

<Current state, the problem, evidence (data, incidents, user feedback). Link requirements.>

## Goals

- <Measurable goal>

## Non-goals

- <Explicitly out of scope>

## Proposed design

### Overview

<Diagram + description of the approach.>

```mermaid
flowchart LR
    A[<Component>] --> B[<Component>]
```

### Details

<APIs, data model changes, algorithms, interfaces. Use subsections per component.>

### Data model changes

<Tables/entities added or changed, migrations.>

### API changes

<New/changed endpoints, events; breaking changes flagged.>

## Alternatives considered

| Alternative | Pros | Cons | Why not |
|---|---|---|---|

## Risks and mitigations

| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|

## Security, privacy, compliance

<Data handled, access, threats, regulatory impact.>

## Performance and scalability

<Expected load, limits, benchmarks.>

## Rollout plan

<Phases, feature flags, migration, backward compatibility, rollback plan.>

## Testing and observability

<Test strategy; metrics, logs, alerts, dashboards to add.>

## Open questions

- [ ] <Question> (owner: <name>, due: <date>)

## Decision

<Filled in when decided: outcome, date, who decided, resulting ADRs.>
