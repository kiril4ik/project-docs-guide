---
id: PRD-<NN>
title: <Feature name>
status: draft               # draft | review | approved | in-development | shipped | archived
owner: <product manager>
reviewers: [<eng lead>, <design>, <qa>]
target_release: <version / quarter>
created: <YYYY-MM-DD>
updated: <YYYY-MM-DD>
links:
  brd: <link>
  designs: <figma link>
  epic: <tracker link>
---

<!-- TEMPLATE: Product Requirements Document. Copy to requirements/<domain>/<feature>.md (or product/features/<feature>.md). Aim for 2–6 pages. Delete this comment. -->

# PRD: <Feature name>

> **Status:** 🟡 Draft · **Owner:** <name> · **Target:** <release>

## 1. Problem

<Who has what problem, how we know (data, research, feedback), and why now.>

## 2. Goals and non-goals

**Goals**

- <Outcome, ideally measurable>

**Non-goals**

- <What this feature deliberately does not do>

## 3. Users and personas

| Persona | Need | Frequency |
|---|---|---|
| <Support agent> | <issue partial refunds quickly> | <daily> |

## 4. User journeys

<Narrative of the main flow(s), step by step from the user's perspective. Add a diagram if useful.>

## 5. Requirements

| ID | Requirement | Priority | Notes |
|---|---|---|---|
| FR-<DOM>-01 | <The system lets a support agent …> | P0 | |
| FR-<DOM>-02 | | P1 | |

Priority: P0 = must for launch, P1 = should, P2 = nice to have.

User stories with acceptance criteria: <link to tracker epic or stories file>.

## 6. Business rules

| Rule | Link |
|---|---|
| <Refunds > €500 need approval> | [BR-PAY-04](<path to rules catalog>#br-pay-04) |

<Link to existing rules; define new rules in the rules catalog, not here.>

## 7. Non-functional requirements

| Category | Requirement |
|---|---|
| Performance | <p95 < 300 ms> |
| Security / privacy | |
| Accessibility | <WCAG 2.2 AA> |
| Audit / compliance | |

## 8. Design

<Links to designs; key screens; states (empty, loading, error).>

## 9. Analytics and success metrics

| Metric | Baseline | Target | How measured |
|---|---|---|---|

## 10. Release plan

<Phases, feature flag, rollout %, migration, communication (release notes, support training).>

## 11. Dependencies and risks

| Item | Type | Owner | Mitigation |
|---|---|---|---|

## 12. Open questions

- [ ] <Question> (owner: <name>, due: <date>)

## 13. Changelog

| Date | Change | By |
|---|---|---|
