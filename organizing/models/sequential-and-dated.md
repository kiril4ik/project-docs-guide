# Model: Sequential & Dated Records

> **What:** Documents identified by a sequence number (`0012-use-stripe.md`) or a date (`2026-10-09-checkout-outage.md`), stored flat in one folder and listed by an index.
> **Read when:** you keep a series of records that are created over time and rarely changed: ADRs, RFCs, postmortems, meeting notes, release notes, requirement IDs.

## TL;DR

- Use **numbers** when order and stable IDs matter (ADRs, RFCs). Use **dates** when time matters (postmortems, meetings, release notes).
- Records are **append-only**: new files are added, and old ones are superseded or archived, never rewritten.
- Always keep an **index** (`README.md`) with ID, title, status and date. File listings alone aren't enough.
- This is a **folder-level pattern**, used inside any project model.

---

## Numbered records

```
architecture/decisions/
├── README.md
├── 0001-record-architecture-decisions.md
├── 0002-use-postgresql.md
├── 0003-modular-monolith.md
├── 0004-use-rabbitmq-for-async.md
└── 0005-replace-rabbitmq-with-kafka.md   (supersedes 0004)
```

| Rule | Why |
|---|---|
| Zero-pad to 4 digits: `0001` | Correct sorting up to 9999 |
| Number + kebab-case title | Human-readable and unique |
| Never reuse or renumber | IDs are referenced from code, PRs, other docs |
| Title in file = title in heading | `# ADR-0005: Replace RabbitMQ with Kafka` |
| Superseding = new file + status update on old one | History stays intact |

### Avoiding number collisions

Two people creating `0006` in parallel branches is common. Options:

- Reserve numbers in the index via a tiny PR first.
- Use the next number at **merge** time (rename during review).
- Use **date-based IDs** instead: `2026-10-09-use-kafka.md`.
- Use tooling (`adr-tools`, `log4brains`) that allocates numbers.

## Dated records

```
operations/postmortems/
├── README.md
├── 2026-08-02-db-failover-delay.md
└── 2026-09-18-checkout-outage.md

meetings/
├── 2026-10-01-sprint-planning.md
└── 2026-10-08-architecture-sync.md

release-notes/
├── 2026-09.md
└── 2026-10.md
```

- Use **ISO 8601** (`YYYY-MM-DD`). It sorts correctly and isn't ambiguous across countries.
- With many files, group by **year** (`2026/`). Avoid month folders unless volume is very high.

## The index page

```markdown
# Architecture Decision Records

| ID | Title | Status | Date |
|---|---|---|---|
| [0005](0005-replace-rabbitmq-with-kafka.md) | Replace RabbitMQ with Kafka | ✅ accepted | 2026-07-11 |
| [0004](0004-use-rabbitmq-for-async.md) | Use RabbitMQ for async | ♻️ superseded by 0005 | 2025-02-03 |
| [0003](0003-modular-monolith.md) | Modular monolith | ✅ accepted | 2024-11-20 |
```

Newest first is usually more useful for postmortems and meetings. Oldest first suits ADRs, which are read as a story. Pick one order and keep it.

## Requirement IDs (sequence without files)

Not every sequence needs one file per item. Business rules and requirements usually live as **rows in a table** with stable IDs (`BR-PAY-04`, `FR-PAY-012`). See [business-requirements](../../doc-types/business-requirements.md#business-rules-catalog). The same rules apply: never reuse an ID, and deprecate rather than delete.

## Pros and cons

| ✅ Pros | ❌ Cons |
|---|---|
| Stable, citable IDs | Unreadable without an index |
| Natural history / timeline | Number collisions in parallel work |
| Trivial to add new records | Finding "the current decision on X" needs the index or search |

## Best for

ADRs, RFCs, postmortems, meeting notes, release notes, changelogs, requirement and rule IDs.

## Avoid when

Living docs (guides, reference, overviews). Numbering them suggests order and immutability that doesn't exist.

---

**Related:** [by-lifecycle](by-lifecycle.md) · [naming-conventions](../naming-conventions.md) · [architecture-docs](../../doc-types/architecture-docs.md#architecture-decision-records-adrs)
**Up:** [Organizing](../README.md)
