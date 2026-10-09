---
alert: <AlertName exactly as in the alerting tool>
service: <service>
severity: <SEV-1 | SEV-2 | SEV-3>
owner: <team>
last_reviewed: <YYYY-MM-DD>
last_tested: <YYYY-MM-DD>
---

<!-- TEMPLATE: Runbook. Copy to operations/runbooks/<alert-name>.md and link it from the alert's runbook_url. Mitigation first, diagnosis second. Delete this comment. -->

# Alert: <AlertName>

**What users experience:** <e.g. checkout fails with an error page>
**Severity:** <SEV-x> · **Escalate after:** <15 min without mitigation>

## 1. Quick mitigation (do this first)

1. <Check whether a deploy happened in the last 30 min: link to deploy log>
2. If yes, roll back:

   ```bash
   <rollback command>
   ```

3. <Other fast mitigation: toggle feature flag, scale up, fail over>

## 2. Diagnosis

| Check | Where / command | Healthy looks like |
|---|---|---|
| <Error rate> | <dashboard link> | << 1%> |
| <Logs> | `<log query>` | <no `ERROR` from service X> |
| <Dependency status> | <status page link> | <operational> |

## 3. Resolution

### Cause A: <e.g. payment provider outage>

1. <step>
2. <step>

### Cause B: <e.g. database connection pool exhausted>

1. <step>

   ```bash
   <command>
   ```

   ⚠️ <Warning for destructive steps>

## 4. Verify

- [ ] <Error rate back below threshold for 10 min>
- [ ] <Synthetic check green>

## 5. Escalation

| After | Contact |
|---|---|
| <15 min> | <secondary on-call / team channel> |
| <30 min or data loss risk> | <incident commander, engineering manager> |

## 6. After the incident

- Open a postmortem if SEV-1/2: [template](<path to postmortem template>)
- Update this runbook with anything that was missing.

## Background

<Optional: why this alert fires, architecture link, past incidents.>
