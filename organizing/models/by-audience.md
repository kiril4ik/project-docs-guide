# Model: Organize by Audience

> **What:** Top-level folders are named after *who reads them*: developers, users, operators, business, partners.
> **Read when:** your readers are distinct groups with different goals and vocabulary, who rarely need each other's docs.

## TL;DR

- Readers pick their door by **role**, and everything behind that door is relevant to them.
- Excellent for products with **external users and internal engineers**, or for platforms with separate **operator** and **developer** readers.
- Weak spot: **duplication**. Some facts matter to several audiences. Keep each fact in one place and link to it.

---

## What it looks like

```
docs/
├── README.md                  "Choose your path" landing page
├── users/                     end users / customers
│   ├── getting-started.md
│   ├── how-to/
│   └── faq.md
├── developers/                people building on or working in the code
│   ├── setup.md
│   ├── architecture/
│   └── api/
├── operators/                 people running/hosting it
│   ├── installation.md
│   ├── configuration.md
│   └── runbooks/
├── business/                  product, sales, compliance
│   ├── requirements/
│   └── policies/
└── shared/                    facts used by several audiences
    └── glossary.md
```

Landing page pattern:

```markdown
# Documentation

| I am a... | Start here |
|---|---|
| 👤 User of the app | [User guide](users/getting-started.md) |
| 👩‍💻 Developer | [Developer setup](developers/setup.md) |
| 🛠 Operator / admin | [Installation](operators/installation.md) |
| 📈 Product / business | [Requirements](business/requirements/README.md) |
```

## Pros and cons

| ✅ Pros | ❌ Cons |
|---|---|
| Readers find their section instantly | Same fact needed by several audiences → duplication risk |
| Each section can use the right tone and depth | People with several roles have to look in several places |
| Easy to publish one audience separately (public user docs) | Domain ownership spread across audience folders |
| Clear for reviewers (the users section is reviewed by support) | Tricky when audiences overlap a lot (devs = operators in DevOps teams) |

## Best for

- Products with **public users + internal team** (SaaS, apps).
- Self-hosted / open-source software (users, operators, contributors).
- Platforms and internal developer platforms (consumers vs maintainers).
- Organizations where business and engineering docs are read by different people.

## Avoid when

- The team is small and everyone reads everything (→ [by-doc-type](by-doc-type.md)).
- Audiences overlap heavily, for example a DevOps team that both builds and runs.
- You can't define audiences crisply. If people argue "is this for devs or ops?", the split will drift.

## How it fails (and the fix)

| Symptom | Fix |
|---|---|
| Setup steps copied into `developers/` and `operators/` | Put them in `shared/` (or the more specific audience) and link from the other |
| A `shared/` folder grows huge | You probably need [by-doc-type](by-doc-type.md) or [hybrid](hybrid.md) as the primary instead |
| Internal info leaks into `users/` | Use a hard split, separate repo or publish pipeline: [internal-vs-public](../internal-vs-public.md) |

## Common variants

- **Two-audience split:** `public/` and `internal/`, or `user-guide/` and `dev-guide/`. This is the simplest and the most common.
- **Audience → Diátaxis:** `users/tutorials/`, `users/how-to/`, `users/reference/`. This suits large product docs.
- **Audience as separate sites:** a user help center, a developer portal and an internal handbook. Each can use its own model inside.

## Migrating

- **To this model:** list audiences ([audiences](../../foundations/audiences.md)), tag every existing doc with its main audience, then move docs and create `shared/` for the rest.
- **Away from it:** usually toward [hybrid](hybrid.md): keep an audience split only at the **public vs internal** level and use type or domain inside.

---

**Related:** [audiences](../../foundations/audiences.md) · [internal-vs-public](../internal-vs-public.md) · [diataxis](diataxis.md)
**Up:** [Organizing](../README.md)
