# Templates

> **What:** Copy-paste starter files for the most common project documents.
> **Read when:** you're creating a new document. Copy the template, rename it, and replace every `<placeholder>`.

## How to use

1. Find the doc type in the table below. Not sure which type you need? See the [doc-types catalog](../doc-types/README.md).
2. Copy the file to its location in your project ([folder-structures](../organizing/folder-structures.md)).
3. Delete the `<!-- TEMPLATE ... -->` comment at the top.
4. Replace every `<placeholder>`, and **delete sections that don't apply**. Don't leave them empty.
5. Add the doc to its folder's `README.md` index.

> Each template is a raw Markdown file. Open it in an editor (not the rendered view) to copy it exactly.

## Index

### Developer

| Template | Copy to | Guide |
|---|---|---|
| [readme-template.md](readme-template.md) | `README.md` (repo root) | [developer-docs](../doc-types/developer-docs.md#root-readmemd) |
| [module-readme-template.md](module-readme-template.md) | `<module>/README.md` | [co-located](../organizing/models/co-located.md) |
| [contributing-template.md](contributing-template.md) | `CONTRIBUTING.md` | [developer-docs](../doc-types/developer-docs.md#contributingmd) |
| [changelog-template.md](changelog-template.md) | `CHANGELOG.md` | [developer-docs](../doc-types/developer-docs.md#changelogmd) |
| [docs-index-template.md](docs-index-template.md) | `<docs-root>/README.md` | [navigation-and-metadata](../organizing/navigation-and-metadata.md#the-docs-root-index) |

### Architecture

| Template | Copy to | Guide |
|---|---|---|
| [adr-template.md](adr-template.md) | `architecture/decisions/NNNN-title.md` | [architecture-docs](../doc-types/architecture-docs.md#architecture-decision-records-adrs) |
| [rfc-design-doc-template.md](rfc-design-doc-template.md) | `rfcs/NNNN-title.md` | [architecture-docs](../doc-types/architecture-docs.md#rfcs-and-design-docs) |

### Business / requirements

| Template | Copy to | Guide |
|---|---|---|
| [brd-template.md](brd-template.md) | `requirements/brd-<initiative>.md` | [business-requirements](../doc-types/business-requirements.md#brd-business-requirements-document) |
| [prd-template.md](prd-template.md) | `requirements/<domain>/<feature>.md` | [business-requirements](../doc-types/business-requirements.md#prd-product-requirements-document) |
| [user-story-template.md](user-story-template.md) | issue tracker or `requirements/<feature>/stories/` | [business-requirements](../doc-types/business-requirements.md#user-stories) |
| [use-case-template.md](use-case-template.md) | `requirements/use-cases/UC-NN-title.md` | [business-requirements](../doc-types/business-requirements.md#use-cases) |
| [business-rules-template.md](business-rules-template.md) | `requirements/rules/<domain>.md` | [business-requirements](../doc-types/business-requirements.md#business-rules-catalog) |

### API

| Template | Copy to | Guide |
|---|---|---|
| [api-endpoint-template.md](api-endpoint-template.md) | `api/reference/<resource>.md` (if not generated) | [api-docs](../doc-types/api-docs.md#what-every-endpoint-page-must-include) |

### Operations

| Template | Copy to | Guide |
|---|---|---|
| [runbook-template.md](runbook-template.md) | `operations/runbooks/<alert-name>.md` | [operations-docs](../doc-types/operations-docs.md#runbooks) |
| [postmortem-template.md](postmortem-template.md) | `operations/postmortems/YYYY-MM-DD-title.md` | [operations-docs](../doc-types/operations-docs.md#incident-postmortems) |

### User / guides

| Template | Copy to | Guide |
|---|---|---|
| [tutorial-template.md](tutorial-template.md) | `tutorials/<title>.md` | [page-patterns](../writing/page-patterns.md#tutorial) |
| [how-to-template.md](how-to-template.md) | `how-to/<task>.md` | [page-patterns](../writing/page-patterns.md#how-to-guide) |

### AI agents

| Template | Copy to | Guide |
|---|---|---|
| [agents-md-template.md](agents-md-template.md) | `AGENTS.md` (repo root) | [ai-agent-docs](../doc-types/ai-agent-docs.md) |

---

**Up:** [Guide home](../README.md) · **Previous section:** [Writing](../writing/README.md)
