# Writing Process

> **What:** A repeatable process for producing a document: plan, outline, draft, review, publish, maintain.
> **Read when:** before writing any doc longer than one screen.

## TL;DR

- **Plan (5 min):** audience, goal, doc type, location. Write them down.
- **Outline before drafting.** Headings only, and get early feedback on those.
- **Draft fast, then edit hard.** Cut about 30%.
- **Test it:** follow your own steps on a clean environment, or have a newcomer do it.
- **Review in a PR**, with a checklist.
- **Assign an owner** and a review date when you publish.

---

## 1. Plan

Fill in this card at the top of your draft (delete it or keep it as front matter later):

```markdown
<!--
Audience:   new backend developers
Goal:       run the billing service locally and process a test payment
Doc type:   how-to guide          (see doc-types/README.md)
Location:   docs/getting-started/billing-local.md
Owner:      team-billing
Success:    a new dev completes it in <20 min without asking for help
-->
```

If you can't fill in **Goal** in one sentence, the doc isn't ready to be written.

## 2. Research

- Collect facts from code, specs, existing docs, tickets and experts.
- Find what **already exists**. Link to it instead of rewriting it (single source of truth).
- Note open questions, and don't guess. Write `TODO(@owner): confirm timeout value` and resolve it before publishing.

## 3. Outline

Write the headings first, using the [page pattern](page-patterns.md) for your doc type:

```markdown
# Run billing locally
## Prerequisites
## Start dependencies
## Configure Stripe test keys
## Run the service
## Process a test payment
## Troubleshooting
```

Share the outline for a 2-minute sanity check. That's the cheapest moment to catch a wrong scope.

## 4. Draft

- Write quickly, and don't polish yet.
- Fill each section with: **what to do → example → expected result**.
- Use real commands, real requests and real field names.
- Mark gaps with `TODO`.

## 5. Edit

Make one pass for each of these:

| Pass | Look for |
|---|---|
| **Structure** | Does the order match the reader's path? Can a scanner get the point from headings + TL;DR alone? |
| **Cut** | Remove history, hedging, repetition, "simply", "just", "obviously" |
| **Clarity** | Short sentences, active voice, one idea per paragraph ([style-guide](style-guide.md)) |
| **Accuracy** | Every command/version/path checked |
| **Links** | Relative, working, descriptive text |
| **Consistency** | Terms match the glossary; formatting matches the rest of the docs |

## 6. Test

| Doc type | How to test |
|---|---|
| Tutorial / setup | Follow it on a clean machine or container, or watch a newcomer follow it |
| How-to / runbook | Execute the steps in staging; drill runbooks |
| Reference | Compare with the spec/code; generate it if possible |
| Requirements | QA can derive test cases; stakeholders confirm in review |
| API examples | Run them (ideally in CI) |

## 7. Review

Open a PR. Reviewers use this checklist:

```markdown
- [ ] Audience and goal are clear in the first lines
- [ ] Correct doc type and location
- [ ] Facts are accurate (subject-matter expert reviewed)
- [ ] Steps tested
- [ ] No duplication of existing docs (links instead)
- [ ] Follows style guide and page pattern
- [ ] Links work; images have alt text
- [ ] Front matter: owner, status, last_reviewed
- [ ] Linked from the folder index
- [ ] No secrets / internal-only info in public docs
```

Get reviewers in two roles if you can: a **subject expert** (is it correct?) and a **target reader** (is it usable?).

## 8. Publish

- Merge, add the doc to the folder index, and announce it if relevant.
- Set `status: active` and `last_reviewed`.

## 9. Maintain

- Update it in the same PR as related code changes.
- Re-review on the schedule ([maintenance](maintenance.md)).
- When readers ask a question the doc should answer, **fix the doc** as well as answering.

---

**Related:** [style-guide](style-guide.md) · [page-patterns](page-patterns.md) · [maintenance](maintenance.md)
**Up:** [Writing](README.md)
