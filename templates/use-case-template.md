---
id: UC-<NN>
title: <Goal of the actor, e.g. "Issue refund">
status: draft
owner: <BA / PM>
---

<!-- TEMPLATE: Use case. Copy to requirements/use-cases/UC-NN-short-title.md. Use for flows with several actors or many alternative paths. Delete this comment. -->

# UC-<NN>: <Title>

| Field | Value |
|---|---|
| **Primary actor** | <role> |
| **Secondary actors** | <other roles / systems> |
| **Goal** | <what the actor wants to achieve> |
| **Trigger** | <event that starts the use case> |
| **Preconditions** | <what must be true before> |
| **Postconditions (success)** | <state after success> |
| **Postconditions (failure)** | <state after failure> |
| **Business rules** | <BR-IDs> |
| **Related** | <PRD, stories, screens> |

## Main success scenario

1. <Actor> <does something>.
2. System <responds>.
3. <Actor> <does something>.
4. System <responds>. Use case ends.

## Alternative flows

**3a. <Condition, e.g. amount > €500>**

1. System <does something different>.
2. Continue at step <N> / use case ends.

## Exceptions

**E1. <Error condition, e.g. payment provider unavailable>**

1. System <shows/does>.
2. <Recovery>.

## Notes

- <Frequency, performance expectations, open questions>
