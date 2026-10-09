# Internal vs Public Docs

> **What:** How to keep internal documentation (architecture, runbooks, decisions) separate from published documentation (user guides, public API docs) so nothing leaks and both stay maintainable.
> **Read when:** any part of your docs is published outside the team, such as an open-source project, a public API or a customer help center.

## TL;DR

- Make visibility a **hard boundary** (folder or repo), not just a metadata flag.
- **Publish only from an allow-listed folder.** The build should never scan everything and filter.
- Internal docs may **link to** public docs, but never the other way round.
- Review public docs for **secrets, internal hostnames, customer data and unannounced features**.

---

## Three separation levels

| Level | Structure | Isolation | Use when |
|---|---|---|---|
| **1. Folder split** | `docs/public/` + `docs/internal/` in one repo | Medium: relies on the build config | Private repo, public docs site built from `public/` only |
| **2. Separate repos** | `product-docs` (public) + `product` (private) | Strong | Open-source docs with a closed-source product, or separate docs team |
| **3. Separate systems** | Public docs site + internal wiki/handbook | Strongest | Large orgs, compliance requirements |

## Folder split example

```
docs/
├── README.md                 explains the split
├── public/                   ⬅ ONLY this folder is published
│   ├── user-guide/
│   ├── api/
│   └── changelog.md
└── internal/                 never published
    ├── architecture/
    ├── decisions/
    ├── runbooks/
    └── requirements/
```

Docs site config points **only** at `docs/public/`:

```yaml
# mkdocs.yml (example)
docs_dir: docs/public
```

## What must never be public

| Category | Examples |
|---|---|
| Secrets & credentials | API keys, passwords, tokens (even "expired" ones) |
| Internal infrastructure | Hostnames, IPs, internal URLs, cloud account IDs, network diagrams |
| Security details | Unpatched vulnerabilities, security architecture specifics |
| Customer & personal data | Names, emails, IDs in examples or screenshots |
| Business-confidential | Pricing strategy, unannounced features, contracts, incident details with customer names |
| Internal people/process | On-call phone numbers, private Slack channels |

✅ Use **obviously fake data** in public examples: `example.com`, `sk_test_...`, "Jane Doe", and the documentation IP ranges `192.0.2.0/24` and `198.51.100.0/24`.

## Safeguards

- Run **secret scanning** in CI on docs too (gitleaks, trufflehog, GitHub secret scanning).
- Add a **link check** that fails if public docs link into `internal/`.
- Use **CODEOWNERS**: public docs need a docs/product reviewer.
- Add a **PR template checkbox**: "No internal-only information in public docs."

---

**Related:** [storage-locations](storage-locations.md) · [by-audience](models/by-audience.md) · [dimensions](dimensions.md#visibility-the-exception)
**Up:** [Organizing](README.md)
