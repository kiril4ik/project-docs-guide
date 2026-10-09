<!-- TEMPLATE: CONTRIBUTING.md. Copy to the repository root (or .github/). Delete this comment. -->

# Contributing to <project>

Thanks for contributing! This guide explains how to set up, make changes, and get them merged.

## Development setup

Follow [Getting started](<docs-root>/getting-started/README.md). In short:

```bash
<install command>
<run command>
<test command>
```

## Workflow

1. Create a branch from `<main>`: `<type>/<short-description>` (e.g. `feat/partial-refunds`, `fix/invoice-rounding`).
2. Make small, focused commits. Format: <Conventional Commits / team format>, e.g. `feat(billing): add partial refunds`.
3. Open a pull request and fill in the template.

## Code style

- Formatting and linting are automated: `<lint command>`, `<format command>`.
- Project conventions (patterns, naming, error handling): [conventions](<docs-root>/development/conventions.md).

## Tests

- Run all tests: `<test command>`
- <Coverage or test-type expectations, e.g. "New business rules need unit tests referencing the rule ID">

## Pull requests

- Keep PRs under <~400> changed lines where possible.
- CI must pass: <list checks>.
- Required reviewers: <rule, or "see CODEOWNERS">.

## Documentation changes

Update docs **in the same PR** when you:

- change a public API → `<path to API spec/docs>`
- add or change configuration → `.env.example` + `<config doc>`
- make a significant technical decision → new ADR in `<docs-root>/architecture/decisions/`
- change a business rule → `<docs-root>/requirements/rules/`
- change user-visible behavior → `CHANGELOG.md` under **Unreleased**

## Reporting bugs and requesting features

<Where and how: issue templates, labels, security issues → SECURITY.md.>

## Getting help

<Channel, maintainers, office hours.>
