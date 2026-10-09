# Further Reading

> **What:** Well-known, widely cited articles, guides, specs, books and examples on every topic this guide covers, grouped by topic.
> **Read when:** you want to go deeper than this guide, or you want the original source behind a recommendation.

## TL;DR: start with these 10

| # | Resource | Why |
|---|---|---|
| 1 | [Diátaxis](https://diataxis.fr/) | The framework for tutorials / how-to / reference / explanation |
| 2 | [Write the Docs: Documentation Guide](https://www.writethedocs.org/guide/) | Community knowledge base on all things docs |
| 3 | [Google Technical Writing courses](https://developers.google.com/tech-writing) | Free, short, practical writing training for engineers |
| 4 | [Google developer documentation style guide](https://developers.google.com/style) | The most-used style reference for technical docs |
| 5 | [Documenting Architecture Decisions](https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions) by Michael Nygard | The original ADR article |
| 6 | [The C4 model](https://c4model.com/) | How to draw architecture diagrams at the right zoom level |
| 7 | [Design Docs at Google](https://www.industrialempathy.com/posts/design-docs-at-google/) | How and why to write design docs before building |
| 8 | [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) | The standard changelog format |
| 9 | [Docs as Code](https://www.writethedocs.org/guide/docs-as-code/) (Write the Docs) | Why docs belong in Git with the code |
| 10 | [AGENTS.md](https://agents.md/) | The open format for AI coding agent instructions |

Links checked on 2026-10-09. External sites change, so if a link breaks, search for the title.

---

## 1. Documentation frameworks and principles

| Resource | Source | Why read it | Guide page |
|---|---|---|---|
| [Diátaxis](https://diataxis.fr/) | Daniele Procida | The four-quadrant model behind most modern product docs | [diataxis](organizing/models/diataxis.md) |
| [The Documentation System](https://docs.divio.com/documentation-system/) | Divio | The earlier, shorter write-up of the same idea, a good 15-minute intro | [diataxis](organizing/models/diataxis.md) |
| [Docs as Code](https://www.writethedocs.org/guide/docs-as-code/) | Write the Docs | Rationale and practices for treating docs like code | [principles](foundations/principles.md#3-docs-as-code) |
| [A beginner's guide to writing documentation](https://www.writethedocs.org/guide/writing/beginners-guide-to-docs/) | Write the Docs | Why to write docs and what a minimal set looks like | [developer-docs](doc-types/developer-docs.md) |
| [Readme Driven Development](https://tom.preston-werner.com/2010/08/23/readme-driven-development.html) | Tom Preston-Werner | Classic essay: write the README before the code | [developer-docs](doc-types/developer-docs.md#root-readmemd) |
| [The Good Docs Project](https://www.thegooddocsproject.dev/) | Community | Open-source templates and guides for many doc types | [templates](templates/README.md) |

## 2. Writing and style

| Resource | Source | Why read it | Guide page |
|---|---|---|---|
| [Technical Writing One & Two](https://developers.google.com/tech-writing) | Google | Short free courses: sentences, lists, paragraphs, audience, organizing | [style-guide](writing/style-guide.md) |
| [Developer documentation style guide](https://developers.google.com/style) | Google | Detailed rules for voice, formatting, code, links, accessibility | [style-guide](writing/style-guide.md) |
| [Word list](https://developers.google.com/style/word-list) | Google | Which terms to use and avoid | [style-guide](writing/style-guide.md#terminology) |
| [Microsoft Writing Style Guide](https://learn.microsoft.com/en-us/style-guide/welcome/) | Microsoft | Second major style reference, strong on tone and global English | [style-guide](writing/style-guide.md) |
| [GitLab documentation style guide](https://docs.gitlab.com/development/documentation/styleguide/) | GitLab | A real-world docs-as-code style guide used by hundreds of contributors | [style-guide](writing/style-guide.md) |
| [How users read on the web](https://www.nngroup.com/articles/how-users-read-on-the-web/) | Nielsen Norman Group | The research behind "write for scanning" | [principles](foundations/principles.md#5-write-for-scanning) |
| [F-shaped pattern of reading](https://www.nngroup.com/articles/f-shaped-pattern-reading-web-content/) | Nielsen Norman Group | Why the first words of headings and paragraphs matter | [style-guide](writing/style-guide.md#headings) |
| [Plain language guidelines](https://www.plainlanguage.gov/guidelines/) | U.S. plainlanguage.gov | Clear-writing rules, especially useful for business and user docs | [user-docs](doc-types/user-docs.md#writing-for-end-users) |

## 3. Markdown and diagrams

| Resource | Source | Why read it | Guide page |
|---|---|---|---|
| [Markdown Guide](https://www.markdownguide.org/) | Matt Cone | Friendly reference for basic and extended syntax | [markdown-essentials](foundations/markdown-essentials.md) |
| [CommonMark tutorial](https://commonmark.org/help/tutorial/) | CommonMark | 10-minute interactive intro to standard Markdown | [markdown-essentials](foundations/markdown-essentials.md) |
| [GitHub Flavored Markdown spec](https://github.github.com/gfm/) | GitHub | Exact behavior of tables, task lists, autolinks | [markdown-essentials](foundations/markdown-essentials.md#github-flavored-markdown-gfm-extras) |
| [Basic writing and formatting syntax](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax) | GitHub Docs | Alerts, anchors, footnotes and more as GitHub renders them | [markdown-essentials](foundations/markdown-essentials.md) |
| [Mermaid documentation](https://mermaid.js.org/) | Mermaid | All diagram types and syntax | [diagrams-and-visuals](writing/diagrams-and-visuals.md) |
| [Include diagrams in Markdown with Mermaid](https://github.blog/developer-skills/github/include-diagrams-markdown-files-mermaid/) | GitHub Blog | How Mermaid works on GitHub | [diagrams-and-visuals](writing/diagrams-and-visuals.md) |

## 4. README, changelog and repository files

| Resource | Source | Why read it | Guide page |
|---|---|---|---|
| [Make a README](https://www.makeareadme.com/) | Danny Guo | What a README should contain, with a template | [developer-docs](doc-types/developer-docs.md#root-readmemd) |
| [Awesome README](https://github.com/matiassingers/awesome-readme) | Community | Curated list of excellent READMEs to learn from | [readme-template](templates/readme-template.md) |
| [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) | Olivier Lacan | Changelog format and principles | [developer-docs](doc-types/developer-docs.md#changelogmd) |
| [Semantic Versioning](https://semver.org/) | Tom Preston-Werner | What version numbers communicate | [developer-docs](doc-types/developer-docs.md#changelogmd) |
| [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) | Community | Commit format that enables generated changelogs | [contributing-template](templates/contributing-template.md) |
| [Default community health files](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file) | GitHub Docs | CONTRIBUTING, SECURITY, CODE_OF_CONDUCT and where GitHub finds them | [process-docs](doc-types/process-docs.md#standard-repository-files) |

## 5. API documentation

| Resource | Source | Why read it | Guide page |
|---|---|---|---|
| [OpenAPI Specification (latest)](https://spec.openapis.org/oas/latest.html) | OpenAPI Initiative | The REST API contract format | [api-docs](doc-types/api-docs.md#spec-first-openapi) |
| [Learn OpenAPI](https://learn.openapis.org/) | OpenAPI Initiative | Beginner-friendly guide to writing OpenAPI | [api-docs](doc-types/api-docs.md#spec-first-openapi) |
| [AsyncAPI docs](https://www.asyncapi.com/docs) | AsyncAPI Initiative | Documenting event-driven and messaging APIs | [api-docs](doc-types/api-docs.md#event-driven-apis) |
| [Documenting APIs course](https://idratherbewriting.com/learnapidoc/) | Tom Johnson (I'd Rather Be Writing) | The most complete free course on API documentation | [api-docs](doc-types/api-docs.md) |
| [Google API Design Guide](https://cloud.google.com/apis/design) | Google Cloud | API design conventions, including how to document them | [api-docs](doc-types/api-docs.md) |
| [Microsoft REST API Guidelines](https://github.com/microsoft/api-guidelines) | Microsoft | Errors, versioning, pagination conventions | [api-docs](doc-types/api-docs.md#errors) |
| [Zalando RESTful API Guidelines](https://opensource.zalando.com/restful-api-guidelines/) | Zalando | Detailed, widely copied API guidelines | [api-docs](doc-types/api-docs.md) |
| [Spectral](https://stoplight.io/open-source/spectral) / [Redocly CLI](https://redocly.com/docs/cli/) | Stoplight / Redocly | Linting and rendering OpenAPI specs | [maintenance](writing/maintenance.md#automation) |

## 6. Architecture and decisions

| Resource | Source | Why read it | Guide page |
|---|---|---|---|
| [Documenting Architecture Decisions](https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions) | Michael Nygard | The original ADR proposal | [architecture-docs](doc-types/architecture-docs.md#architecture-decision-records-adrs) |
| [ADR GitHub organization](https://adr.github.io/) | ADR community | Overview of ADR formats and tools | [architecture-docs](doc-types/architecture-docs.md#architecture-decision-records-adrs) |
| [MADR](https://adr.github.io/madr/) | ADR community | Markdown ADR template with options and pros/cons | [adr-template](templates/adr-template.md) |
| [Architecture decision record examples](https://github.com/joelparkerhenderson/architecture-decision-record) | Joel Parker Henderson | Many ADR templates and real examples | [adr-template](templates/adr-template.md) |
| [adr-tools](https://github.com/npryce/adr-tools) | Nat Pryce | CLI for creating numbered ADRs | [sequential-and-dated](organizing/models/sequential-and-dated.md) |
| [Scaling the Practice of Architecture, Conversationally](https://martinfowler.com/articles/scaling-architecture-conversationally.html) | Andrew Harmel-Law (martinfowler.com) | ADRs plus the "advice process" for decentralized decisions | [architecture-docs](doc-types/architecture-docs.md) |
| [The C4 model](https://c4model.com/) | Simon Brown | Context, container, component and code diagrams | [architecture-docs](doc-types/architecture-docs.md#c4-model) |
| [Structurizr](https://structurizr.com/) | Simon Brown | C4 diagrams as code | [diagrams-and-visuals](writing/diagrams-and-visuals.md#diagram-tools) |
| [arc42](https://arc42.org/) | Gernot Starke, Peter Hruschka | Full architecture documentation template | [architecture-docs](doc-types/architecture-docs.md#architecture-overview) |
| [Design Docs at Google](https://www.industrialempathy.com/posts/design-docs-at-google/) | Malte Ubl | Structure, value and lifecycle of design docs | [architecture-docs](doc-types/architecture-docs.md#rfcs-and-design-docs) |
| [Software design document guide](https://www.atlassian.com/work-management/knowledge-sharing/documentation/software-design-document) | Atlassian | Practical design-doc outline | [rfc-design-doc-template](templates/rfc-design-doc-template.md) |

**Real RFC processes to study:** [Rust RFCs](https://github.com/rust-lang/rfcs) · [Python PEP 1](https://peps.python.org/pep-0001/) (the PEP process) · [Kubernetes KEPs](https://github.com/kubernetes/enhancements/tree/master/keps)

## 7. Requirements and product docs

| Resource | Source | Why read it | Guide page |
|---|---|---|---|
| [Painless Functional Specifications](https://www.joelonsoftware.com/2000/10/02/painless-functional-specifications-part-1-why-bother/) | Joel Spolsky | Classic 4-part series on why and how to write specs | [business-requirements](doc-types/business-requirements.md) |
| [Product requirements](https://www.atlassian.com/agile/product-management/requirements) | Atlassian | Agile PRD structure | [prd-template](templates/prd-template.md) |
| [PRDs and 1-pagers: examples](https://www.lennysnewsletter.com/p/prds-1-pagers-examples) | Lenny Rachitsky | Real PRD templates from well-known product companies | [prd-template](templates/prd-template.md) |
| [Shape Up: Write the Pitch](https://basecamp.com/shapeup/1.5-chapter-06) | Basecamp (Ryan Singer) | A lean alternative to PRDs: problem, appetite, solution, rabbit holes, no-gos | [business-requirements](doc-types/business-requirements.md#prd-product-requirements-document) |
| [User stories](https://www.atlassian.com/agile/project-management/user-stories) | Atlassian | User stories with examples | [user-story-template](templates/user-story-template.md) |
| [INVEST in Good Stories](https://xp123.com/articles/invest-in-good-stories-and-smart-tasks/) | Bill Wake | Origin of the INVEST checklist | [business-requirements](doc-types/business-requirements.md#user-stories) |
| [Gherkin reference](https://cucumber.io/docs/gherkin/reference/) | Cucumber | Given/When/Then syntax for acceptance criteria | [business-requirements](doc-types/business-requirements.md#acceptance-criteria) |
| [Ubiquitous Language](https://martinfowler.com/bliki/UbiquitousLanguage.html) | Martin Fowler | Why a shared domain vocabulary (glossary) matters | [business-requirements](doc-types/business-requirements.md#domain-glossary) |

## 8. Operations and incidents

| Resource | Source | Why read it | Guide page |
|---|---|---|---|
| [Postmortem Culture: Learning from Failure](https://sre.google/sre-book/postmortem-culture/) | Google SRE Book | Blameless postmortems explained | [operations-docs](doc-types/operations-docs.md#incident-postmortems) |
| [Example Postmortem](https://sre.google/sre-book/example-postmortem/) | Google SRE Book | A complete real-format postmortem | [postmortem-template](templates/postmortem-template.md) |
| [Incident postmortems](https://www.atlassian.com/incident-management/postmortem) | Atlassian | Postmortem process, templates and meeting guide | [postmortem-template](templates/postmortem-template.md) |
| [PagerDuty Incident Response](https://response.pagerduty.com/) | PagerDuty | Open-source incident response docs, a model for runbook-style writing | [runbook-template](templates/runbook-template.md) |

## 9. Organizing knowledge and handbooks

| Resource | Source | Why read it | Guide page |
|---|---|---|---|
| [GitLab Handbook](https://handbook.gitlab.com/) | GitLab | The best-known public company handbook, thousands of Markdown pages organized at scale | [storage-locations](organizing/storage-locations.md#handbook-repo-organization-level) |
| [The PARA Method](https://fortelabs.com/blog/para/) | Tiago Forte | Projects / Areas / Resources / Archive for knowledge bases | [flat-with-metadata](organizing/models/flat-with-metadata.md#para-for-team-or-personal-knowledge-bases) |
| [Backstage TechDocs](https://backstage.io/docs/features/techdocs/) | Spotify / CNCF | Docs-like-code aggregated into a developer portal | [per-service-repo](organizing/models/per-service-repo.md) |
| [Docs for Developers](https://docsfordevelopers.com/) | Bhatti, Corleissen, Lambourne, Nunez, Waterhouse | Book companion site, covering planning, writing, organizing and maintaining docs | [writing-process](writing/writing-process.md) |

## 10. AI agents and LLM-friendly docs

| Resource | Source | Why read it | Guide page |
|---|---|---|---|
| [AGENTS.md](https://agents.md/) | Agentic AI Foundation (Linux Foundation) | The format and the list of supporting tools | [ai-agent-docs](doc-types/ai-agent-docs.md) |
| [Claude Code memory (CLAUDE.md)](https://code.claude.com/docs/en/memory) | Anthropic | How CLAUDE.md files, nesting and `@imports` work | [ai-agent-docs](doc-types/ai-agent-docs.md#agent-instruction-files) |
| [Copilot custom instructions](https://docs.github.com/en/copilot/how-tos/copilot-cli/customize-copilot/add-custom-instructions) | GitHub Docs | `copilot-instructions.md` and path-specific `*.instructions.md` | [ai-agent-docs](doc-types/ai-agent-docs.md#agent-instruction-files) |
| [llms.txt](https://llmstxt.org/) | Jeremy Howard (proposal) | The llms.txt proposal for LLM-readable site indexes | [ai-agent-docs](doc-types/ai-agent-docs.md#llmstxt) |

## 11. Docs-as-code tooling

| Tool | What it does | Guide page |
|---|---|---|
| [Vale](https://vale.sh/) | Prose linter with custom style rules | [maintenance](writing/maintenance.md#automation) |
| [markdownlint](https://github.com/DavidAnson/markdownlint) | Markdown style and structure linter | [maintenance](writing/maintenance.md#automation) |
| [lychee](https://github.com/lycheeverse/lychee) | Fast link checker for Markdown and sites | [maintenance](writing/maintenance.md#automation) |
| [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) | Popular docs site generator for Markdown | [user-docs](doc-types/user-docs.md#tooling) |
| [Docusaurus](https://docusaurus.io/) | Docs site generator with versioning | [by-version](organizing/models/by-version.md) |
| [The Good Docs Project templates](https://github.com/thegooddocsproject/templates) | Community doc templates | [templates](templates/README.md) |

## 12. Books

| Book | Author(s) | Why read it |
|---|---|---|
| [*Docs for Developers*](https://docsfordevelopers.com/) (Apress, 2021) | Jared Bhatti, Zachary Sarah Corleissen, Jen Lambourne, David Nunez, Heidi Waterhouse | The best end-to-end book on engineering documentation |
| [*Docs Like Code*](https://www.docslikecode.com/) | Anne Gentle | Practical docs-as-code workflows with Git and CI |
| *Living Documentation* (Addison-Wesley, 2019) | Cyrille Martraire | Docs generated from and kept in sync with code, DDD-friendly |
| *Every Page Is Page One* (XML Press, 2014) | Mark Baker | Writing self-contained topics for readers arriving from search, which is just as relevant to AI retrieval |
| *Site Reliability Engineering* ([free online](https://sre.google/sre-book/postmortem-culture/)) | Google | Postmortems, on-call and operational docs culture |

## 13. Great documentation to study

Learn by example. Pick one or two that match your project type and look at how they're organized.

| Docs | Study it for |
|---|---|
| [Stripe API reference](https://docs.stripe.com/api) | Reference layout, examples next to every field, error docs |
| [Django documentation](https://docs.djangoproject.com/en/stable/) | Clear separation of tutorials, topic guides, reference and how-tos |
| [Kubernetes documentation](https://kubernetes.io/docs/home/) | Concepts / tasks / tutorials / reference at very large scale |
| [GitLab Handbook](https://handbook.gitlab.com/) | Organizing a company's knowledge in Markdown |
| [Rust RFCs](https://github.com/rust-lang/rfcs) | A mature, numbered proposal process |
| [PagerDuty Incident Response](https://response.pagerduty.com/) | Operational docs written for use under stress |
| [Awesome README](https://github.com/matiassingers/awesome-readme) | README patterns from many projects |

---

**Up:** [Guide home](README.md)
