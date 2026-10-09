# Page Patterns

> **What:** Ready skeletons for each kind of page: tutorial, how-to guide, reference, explanation, overview, decision record, troubleshooting and index.
> **Read when:** you know which doc type you're writing and need its shape. Full copyable files are in [templates](../templates/README.md).

## TL;DR

- Every page starts with the **universal header**: title, one-line purpose, audience, and optionally a TL;DR.
- Each page kind has **one job**. Don't mix a tutorial with a reference.
- Use the patterns below as outlines and fill them with real content.

---

## Universal page header

```markdown
---
owner: team-billing
status: active
last_reviewed: 2026-10-01
---

# <Title that names the topic or task>

> <One sentence: what this page helps the reader do or understand.>
> **Audience:** <who> · **Prerequisites:** <links>

## TL;DR            ← optional for short pages; recommended for long ones
- ...
```

---

## Tutorial

**Job:** teach a beginner by guiding them to a working result. Learning-oriented.

```markdown
# Build your first <thing>

In this tutorial you'll build <result>. It takes about <N> minutes.

## What you'll build
<screenshot or description of the end result>

## Before you start
- <tool + version>
- <account>

## Step 1: <action>
<instruction>
<code>
<what you should see>

## Step 2: <action>
...

## What you've learned
- <concept 1>
- <concept 2>

## Next steps
- <link to how-to guides>
- <link to explanation>
```

✅ One path, no options. Every step produces visible progress. Test it end to end.
❌ No "alternatively…", no deep explanations (link out instead), no assumed knowledge.

## How-to guide

**Job:** help a competent reader complete one specific task. Goal-oriented.

````markdown
# How to <do task>
(or a verb title: "Rotate API keys")

<One sentence on when you'd need this.>

## Prerequisites
- <permissions, versions, prior setup>

## Steps
1. <action>
2. <action>
   ```bash
   <command>
   ```
3. <action>

## Verify
<how to check it worked>

## Troubleshooting
| Problem | Solution |
|---|---|

## Related
- <links>
````

✅ Starts from the goal. Assumes basics. Can mention options briefly ("To do X instead, see…").
❌ No teaching from scratch, no history or theory.

## Reference page

**Job:** describe facts completely and consistently, for looking things up. Information-oriented.

````markdown
# <Thing> reference

<One sentence: what this is.>

## <Item 1>
<Short description.>

| Property | Type | Required | Default | Description |
|---|---|---|---|---|

**Example**
```<lang>
...
```

## <Item 2>
... (identical structure for every item)
````

✅ Same structure for every entry. Complete. Alphabetical or mirrors the product's structure. Generate it if possible.
❌ No instructions or opinions. Link to how-tos and explanations instead.

## Explanation (concept) page

**Job:** build understanding: the why, how it works, and trade-offs. Understanding-oriented.

```markdown
# <Concept / "How X works" / "About X">

<Summary paragraph: what it is and why it matters.>

## How it works
<narrative + diagram>

## Why it's designed this way
<context, constraints, decisions (link ADRs)>

## Trade-offs and alternatives

## Related
```

✅ Discursive prose is fine. Diagrams help. Connect to other concepts.
❌ No step-by-step instructions (link to a how-to).

## Overview page (system, domain, module)

**Job:** orient the reader. What this is, how it fits in, where to go next.

```markdown
# <System / domain / module name>

<What it does in 2–3 sentences.>

- **Owner:** <team>
- **Code:** <paths>
- **Depends on / used by:** <links>

## Context
<diagram>

## Key concepts
<3–7 bullets, linked to glossary>

## Where to go next
| I want to... | Read |
|---|---|
```

## Decision record (ADR)

```markdown
# ADR-<NNNN>: <Decision in active voice>

- **Status:** proposed | accepted | superseded by ADR-XXXX
- **Date:** YYYY-MM-DD
- **Deciders:** <names>

## Context
## Decision
## Alternatives considered
## Consequences
```

Details: [architecture-docs](../doc-types/architecture-docs.md#architecture-decision-records-adrs) · Template: [adr-template](../templates/adr-template.md)

## Troubleshooting page

**Job:** map symptoms to fixes, fast.

```markdown
# Troubleshooting <area>

## <Exact error message or symptom>
**Cause:** <one sentence>
**Fix:**
1. <step>

## <Next symptom>
...
```

✅ Use the **exact error text** as headings, which makes them searchable for humans and AI.
✅ Put the most common problems first.

## Index page (folder README)

**Job:** a menu for the folder.

```markdown
# <Folder topic>

> <What this folder contains.> **Owner:** <team>

| Page | Description |
|---|---|
| [page.md](page.md) | <one line> |
```

See [navigation-and-metadata](../organizing/navigation-and-metadata.md#folder-index-readmemd-pattern).

---

## Matching doc types to patterns

| Doc type | Pattern(s) |
|---|---|
| README (root) | Overview + quick start (mini tutorial) |
| Getting started | Tutorial |
| Runbook | How-to (with mitigation first) |
| API endpoint docs | Reference |
| API quick start | Tutorial |
| Architecture overview | Overview + explanation |
| ADR | Decision record |
| PRD / BRD | Own templates ([templates](../templates/README.md)) |
| Business rules | Reference (table with IDs) |
| FAQ | Troubleshooting-like Q → A |

---

**Related:** [diataxis model](../organizing/models/diataxis.md) · [templates](../templates/README.md) · [style-guide](style-guide.md)
**Up:** [Writing](README.md)
