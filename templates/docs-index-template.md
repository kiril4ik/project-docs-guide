<!-- TEMPLATE: Docs root index. Copy to <docs-root>/README.md. Delete this comment. -->

# <Project> documentation

> Everything about building, running and using <project>. Start with the table below.

## Who these docs are for

| I am... | Start here |
|---|---|
| A new developer | [Getting started](getting-started/README.md) |
| Working on the architecture | [Architecture](architecture/README.md) |
| Integrating with the API | [API](api/README.md) |
| Product / business / QA | [Requirements](requirements/README.md) |
| On call | [Runbooks](operations/runbooks/README.md) |

## Map

| Folder | Contains | Owner |
|---|---|---|
| [getting-started/](getting-started/README.md) | Local setup, configuration, troubleshooting | <team> |
| [architecture/](architecture/README.md) | Overview, diagrams, decisions (ADRs) | <team> |
| [api/](api/README.md) | API reference and guides | <team> |
| [requirements/](requirements/README.md) | PRDs, business rules, NFRs | <team> |
| [operations/](operations/README.md) | Deployment, runbooks, postmortems | <team> |
| [glossary.md](glossary.md) | Shared vocabulary | everyone |

## How these docs are organized

- **Top level = <dimension, e.g. doc type>.** <one line>
- **Second level = <dimension, e.g. domain>** when a folder has more than <15> files.
- **ADRs** are numbered `NNNN-title.md`; **postmortems** are dated `YYYY-MM-DD-title.md`.
- **Module docs** live next to the code: `<path>/README.md`.
- **Metadata:** every doc has `owner`, `status`, `last_reviewed` in front matter.
- **Source of truth:** Markdown in this repo, except <user stories (tracker), meeting notes (wiki)>.
- **Archived** docs are in [archive/](archive/README.md) and are not maintained.

## Contributing to docs

- Templates: <link>
- Style guide: <link>
- Docs change in the same PR as the code they describe.

## Most-used pages

- [<page>](<path>)
- [<page>](<path>)
