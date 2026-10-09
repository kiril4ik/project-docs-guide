---
domain: <domain>
owner: <business owner team>
status: active
last_reviewed: <YYYY-MM-DD>
---

<!-- TEMPLATE: Business rules catalog for one domain. Copy to requirements/rules/<domain>.md. IDs are permanent: never reuse or renumber; deprecate instead. Delete this comment. -->

# Business rules: <Domain>

> Canonical source for <domain> business rules. PRDs, stories, code and tests reference these IDs.
> **ID format:** `BR-<DOMAIN CODE>-<NN>`

## Summary

| ID | Rule | Status |
|---|---|---|
| [BR-<DOM>-01](#br-dom-01) | <short rule> | active |
| [BR-<DOM>-02](#br-dom-02) | <short rule> | deprecated |

---

## BR-<DOM>-01

**Rule:** <One precise, testable statement. e.g. "Refunds above €500.00 require approval by a finance manager before processing.">

| Field | Value |
|---|---|
| Source | <policy, regulation, contract, stakeholder> |
| Rationale | <why the rule exists> |
| Since | <YYYY-MM-DD> |
| Applies to | <channels, products, regions> |
| Exceptions | <none / list> |
| Implemented in | `<path or module>` |
| Tests | `<test file or test IDs>` |

**Examples**

| Input | Expected |
|---|---|
| <Refund €500.00> | <Processed immediately> |
| <Refund €500.01> | <Pending approval> |

---

## BR-<DOM>-02

> 🟠 **Deprecated** since <date>. Replaced by [BR-<DOM>-NN](#br-dom-nn).

**Rule:** <...>
