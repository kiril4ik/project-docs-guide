---
date: <YYYY-MM-DD>
severity: <SEV-1 | SEV-2 | SEV-3>
status: draft               # draft | reviewed | published
authors: [<name>]
services: [<service>]
---

<!-- TEMPLATE: Blameless incident postmortem. Copy to operations/postmortems/YYYY-MM-DD-short-title.md. Focus on systems and processes, not individuals. Immutable once published. Delete this comment. -->

# Postmortem: <Short title> (<YYYY-MM-DD>)

## Summary

<3 sentences: what happened, impact, how it was resolved.>

## Impact

| Metric | Value |
|---|---|
| Duration | <HH:MM> (<start> – <end> UTC) |
| Users affected | <number / %> |
| Failed requests / orders | <number> |
| SLO budget consumed | <%> |
| Revenue / contractual impact | <if known> |

## Timeline (UTC)

| Time | Event |
|---|---|
| <14:02> | <Deploy of v2.3.1 started> |
| <14:09> | <Alert CheckoutHigh5xxRate fired> |
| <14:15> | <On-call acknowledged, started runbook> |
| <14:21> | <Rollback completed; errors dropping> |
| <14:30> | <Incident resolved> |

## Root cause

<Technical cause, explained clearly. Use 5 Whys or similar.>

### Contributing factors

- <e.g. Missing test for currency rounding>
- <e.g. Alert threshold too high, delayed detection>

## Detection and response

- **What went well:** <…>
- **What went badly:** <…>
- **Where we got lucky:** <…>

## Action items

| Action | Type | Owner | Ticket | Due |
|---|---|---|---|---|
| <Add rounding test> | prevent | <name> | <link> | <date> |
| <Lower alert threshold> | detect | <name> | <link> | <date> |
| <Update runbook step 3> | mitigate | <name> | <link> | <date> |

## Lessons learned

- <Short, general lessons for the team>
