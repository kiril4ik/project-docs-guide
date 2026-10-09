# User Docs

> **What:** Docs for people who *use* the product: tutorials, how-to guides, feature reference, FAQ, troubleshooting, release notes and admin guides.
> **Read when:** your product has users outside the dev team, whether customers, internal staff or developers using your library.

## TL;DR

- Organize user docs by **user task**, not by your internal module structure.
- **Diátaxis** works especially well here: tutorials, how-to guides, reference, explanation.
- Use the **user's vocabulary**, with screenshots or examples for every non-trivial step.
- **Release notes** tell users what changed *for them*. That makes them different from the CHANGELOG.
- User docs usually belong on a **docs site** or help center, built from Markdown if possible.

---

## User doc types

| Type | Purpose | Example title |
|---|---|---|
| **Tutorial** | Teach a beginner through a complete first experience | "Build your first invoice in 10 minutes" |
| **How-to guide** | Solve one specific task | "Issue a partial refund" |
| **Feature reference** | Describe every setting/field/option | "Refund settings" |
| **Concept / explanation** | Explain how something works and why | "How refund approvals work" |
| **FAQ** | Quick answers to repeated questions | "Can I refund after 90 days?" |
| **Troubleshooting** | Symptom → cause → fix | "Refund button is greyed out" |
| **Release notes** | What's new and what changed, in user terms | "October 2026 release" |
| **Admin guide** | Setup and management for admins | "Configure approval thresholds" |
| **Installation guide** | For self-hosted/downloadable products | "Install on Ubuntu 24.04" |

How each is shaped: [page-patterns](../writing/page-patterns.md).

---

## Organizing user docs

**Recommended:** Diátaxis at the top, product areas inside.

```
user-guide/
├── README.md                   landing: who it's for, popular tasks, search tips
├── tutorials/
│   └── first-invoice.md
├── how-to/
│   ├── billing/
│   │   ├── issue-refund.md
│   │   └── change-plan.md
│   └── users/
│       └── invite-teammate.md
├── reference/
│   ├── settings.md
│   └── keyboard-shortcuts.md
├── concepts/
│   └── refund-approvals.md
├── troubleshooting.md
├── faq.md
└── release-notes/
    ├── 2026-10.md
    └── 2026-09.md
```

Alternative for large products: **product area at the top**, Diátaxis inside each area. See [diataxis model](../organizing/models/diataxis.md) and [hybrid](../organizing/models/hybrid.md).

---

## Writing for end users

| ✅ Do | ❌ Don't |
|---|---|
| Use names from the UI exactly: **Settings → Billing** | Use internal names: "the BillingConfigService" |
| Start with the goal: "To refund an order…" | Start with background |
| One action per numbered step | Combine three clicks in one sentence |
| Show the expected result after key steps | Leave the user guessing whether it worked |
| Screenshots for complex UI, cropped and annotated | Full-screen screenshots of everything |
| Mention required permissions/plan upfront | Let users discover at step 7 they're not allowed |

---

## Release notes vs CHANGELOG

| | Release notes | CHANGELOG |
|---|---|---|
| Reader | Users, customers, support, sales | Developers, integrators |
| Content | Highlights, benefits, how to use new features | Every notable change |
| Tone | Friendly, benefit-first | Concise, technical |
| Format | Grouped by theme: New, Improved, Fixed | Keep a Changelog categories |

```markdown
## October 2026

### ✨ New: Partial refunds
You can now refund part of an order directly from the order page.
[Learn how →](../how-to/billing/issue-refund.md)

### 🛠 Improved
- Invoice PDFs now show the tax breakdown.

### 🐛 Fixed
- Password reset emails were sometimes sent twice.
```

---

## Tooling

| Need | Options (examples) |
|---|---|
| Docs site from Markdown | MkDocs (Material), Docusaurus, VitePress, Starlight (Astro), mdBook |
| Hosted help center | Intercom, Zendesk Guide, GitBook, Mintlify, ReadMe |
| Versioned docs | Docusaurus versioning, `mike` for MkDocs |
| Search | Built-in search, Algolia DocSearch |

Prefer tools that read **plain Markdown from Git**, so user docs stay docs-as-code.

---

**Related:** [page-patterns](../writing/page-patterns.md) · [diataxis model](../organizing/models/diataxis.md) · [internal-vs-public](../organizing/internal-vs-public.md)
**Up:** [Doc types](README.md)
