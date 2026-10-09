# Operations Docs

> **What:** Docs for running the system in production: environments, deployment, configuration, monitoring, runbooks, incident postmortems, SLOs and disaster recovery.
> **Read when:** the project is deployed anywhere other than a laptop, and certainly before the first on-call shift.

## TL;DR

- Ops docs are read **under stress**. Make them short, numbered and copy-pasteable, with the critical step first.
- Name runbooks after the **alert or symptom** ("High 5xx on checkout"), not the system.
- Every alert should link to **its runbook**.
- Write **blameless postmortems** after incidents, with owned action items.
- **Never** put secrets in docs. Document *where* secrets live and *who* can access them.

---

## The operations doc set

| Doc | Purpose | Location |
|---|---|---|
| Environments | What environments exist, URLs, differences, access | `operations/environments.md` |
| Deployment / release | How code gets to production, how to roll back | `operations/deployment.md` |
| Configuration | All config/env vars, defaults, where set | `operations/configuration.md` (or generated from `.env.example`) |
| Monitoring & alerts | Dashboards, alerts, what each alert means | `operations/monitoring.md` |
| **Runbooks** | Step-by-step response per alert/situation | `operations/runbooks/` |
| **Postmortems** | Learn from incidents | `operations/postmortems/YYYY-MM-DD-title.md` |
| SLOs / SLAs | Reliability targets and error budgets | `operations/slos.md` |
| Backup & disaster recovery | Backup schedule, restore procedure, RTO/RPO | `operations/disaster-recovery.md` |
| Access & on-call | Who is on call, escalation path, access requests | `operations/on-call.md` |
| Infrastructure | IaC layout, cloud accounts, network overview | `operations/infrastructure.md` or co-located with IaC code |

---

## Runbooks

A runbook turns tribal knowledge into a procedure anyone on-call can follow.

### Structure

| Section | Contents |
|---|---|
| Title | The alert name or symptom, exactly as shown in the alerting tool |
| Severity & impact | What users experience |
| **Quick mitigation** | The 1–3 actions that stop the bleeding, **first** |
| Diagnosis | Dashboards, queries, log searches, with links and exact commands |
| Resolution steps | Numbered, copy-pasteable, with expected output |
| Verification | How to confirm it's fixed |
| Escalation | Who to page and when |
| Background | Optional: why this happens, link to architecture |

````markdown
# Alert: CheckoutHigh5xxRate

**Impact:** Customers cannot pay. **Severity:** SEV-1.

## Quick mitigation
1. Check the status page of Stripe: https://status.stripe.com
2. If a deploy happened in the last 30 min, roll back:
   ```bash
   ./scripts/rollback.sh checkout-api
   ```

## Diagnosis
- Dashboard: Grafana → "Checkout / Errors"
- Logs: `service:checkout-api status:5xx` in the last 15 min
...
````

### Runbook rules

- ✅ **Mitigation before diagnosis.** Restore service first, investigate later.
- ✅ Commands are exact and safe to copy. Mark destructive ones with ⚠️.
- ✅ Test runbooks in game days or drills.
- ✅ Link every alert to its runbook (most alerting tools support a `runbook_url` field).
- ❌ "Investigate the logs" isn't a step. Say *which* logs and *what* to look for.

Template: [templates/runbook-template.md](../templates/runbook-template.md)

---

## Deployment docs

Cover: the pipeline overview (diagram), how to release, feature flags, database migrations, **rollback procedure**, release checklist and freeze periods. If the pipeline is fully automated, document what to do **when it fails**.

---

## Incident postmortems

**Blameless**: focus on systems and processes, not on who made a mistake.

| Section | Contents |
|---|---|
| Summary | What happened, in 3 sentences |
| Impact | Duration, users affected, revenue/SLO impact |
| Timeline | Timestamped events (detection → mitigation → resolution) |
| Root cause(s) | Technical + contributing factors (5 Whys or similar) |
| What went well / badly | Detection, response, tooling |
| Action items | Table: action, owner, ticket, due date |

Naming: `postmortems/2026-09-18-checkout-outage.md`. Postmortems are **immutable records**. Track action items in the issue tracker. See [sequential-and-dated](../organizing/models/sequential-and-dated.md).

Template: [templates/postmortem-template.md](../templates/postmortem-template.md)

---

## Configuration docs

Keep one canonical list, ideally generated from or checked against `.env.example` / config schema:

| Variable | Required | Default | Description | Secret? |
|---|---|---|---|---|
| `DATABASE_URL` | ✅ | — | PostgreSQL connection string | ✅ (Vault: `app/db`) |
| `QUEUE_WORKERS` | | `4` | Number of worker processes | |

---

## Where ops docs live

| Option | Good for |
|---|---|
| In the app repo (`operations/`) | Single service, team owns code and ops |
| Co-located with IaC (`infra/README.md`, `infra/runbooks/`) | Platform/infra teams |
| Central ops/SRE handbook repo | Many services, shared on-call, cross-service runbooks |
| Incident tool / wiki | Postmortems, if the org standardizes there; link from repo |

⚠️ Make sure runbooks are reachable **when production is down**. If your docs site is hosted on the same infrastructure, keep a copy in Git, which can still be read from GitHub/GitLab.

---

**Related:** [architecture-docs](architecture-docs.md) · [developer-docs](developer-docs.md) · [storage-locations](../organizing/storage-locations.md)
**Up:** [Doc types](README.md)
