---
id: US-<NN>
feature: <PRD-NN link>
status: ready              # draft | ready | in-progress | done
priority: <P0 | P1 | P2>
estimate: <points>
---

<!-- TEMPLATE: User story with acceptance criteria. Usually goes in the issue tracker; use this file when stories live in the repo (requirements/<feature>/stories/US-NN-title.md). Delete this comment. -->

# US-<NN>: <Short title>

**As a** <role>
**I want** <capability>
**so that** <benefit>.

## Context

<Optional: why this matters, links to PRD section, designs.>

## Acceptance criteria

```gherkin
Scenario: <happy path>
  Given <precondition>
  When <action>
  Then <expected outcome>

Scenario: <alternative / edge case>
  Given <precondition>
  When <action>
  Then <expected outcome>

Scenario: <error case>
  Given <precondition>
  When <action>
  Then <error behavior>
```

## Business rules

- [<BR-ID>](<path>): <one-line summary>

## Out of scope

- <What this story does not cover>

## Notes

- <Design link, technical notes, dependencies>

## Definition of Done

- [ ] Acceptance criteria pass (automated tests reference this story ID)
- [ ] Docs / CHANGELOG updated
- [ ] Reviewed and merged
