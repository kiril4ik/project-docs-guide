# Style Guide

> **What:** Writing rules for clear, consistent, scannable documentation: voice, sentences, headings, lists, tables, code, links and terminology.
> **Read when:** writing or reviewing any doc. Adopt it (or adapt it) as your project's style guide.

## TL;DR

- **Plain, direct, active.** "Run the migration", not "The migration should be run".
- **Short:** sentences under ~25 words, paragraphs of 3–4 sentences.
- **Descriptive headings** in sentence case, which act as a table of contents.
- **Lists for sequences and sets, tables for comparisons, code blocks for anything copyable.**
- **One term per concept.** Define it in the glossary and use it everywhere.

---

## Voice and tone

| ✅ Do | ❌ Don't |
|---|---|
| Address the reader as "you" | "The user should…" / "One must…" |
| Use imperative for instructions: "Click **Save**." | "You might want to click save." |
| Use active voice: "The service sends an email." | "An email is sent by the service." |
| Be confident and specific: "Requests time out after 30 s." | "Requests may possibly time out at some point." |
| Use present tense: "The API returns…" | "The API will return…" |
| Be neutral and inclusive | Idioms, jokes, culture-specific references |

Avoid words that make readers feel bad: *simply, just, easy, obviously, of course*. If it were obvious, they wouldn't be reading the docs.

## Sentences and paragraphs

- One idea per sentence, one topic per paragraph.
- Put the **condition first**: "If the build fails, run `make clean`." This lets readers skip what doesn't apply.
- Put the **most important word early** in headings and list items.
- Expand acronyms on first use: "Architecture Decision Record (ADR)".
- Use numbers, not words, for quantities: "3 retries", "30 seconds".

## Headings

| Rule | ✅ | ❌ |
|---|---|---|
| One H1 per file = title | `# Deploy to production` | Several H1s |
| Don't skip levels | H2 → H3 | H2 → H4 |
| Sentence case | `## Configure the database` | `## Configure The Database` |
| Descriptive, task-based | `## Rotate the API key` | `## Procedure`, `## Misc` |
| Keep them unique within a page | | Two `## Example` sections (breaks anchors) |
| No punctuation at the end | `## Prerequisites` | `## Prerequisites:` |

Test: read only the headings. You should be able to tell what the page covers and in what order.

## Lists

- **Numbered** for sequential steps, **bullets** for unordered items.
- **One action per step.** Put sub-actions in nested lists.
- Use parallel grammar (all verbs, or all nouns).
- Lists of more than about 7 items become hard to scan, so group them or use a table.
- Punctuation: no period for fragments, periods for full sentences. Be consistent within a list.

## Steps (procedures)

```markdown
1. Open **Settings → Billing**.
2. Select **Issue refund**.
3. Enter the amount and select **Confirm**.

   The refund appears in **History** with the status *Pending*.
```

- Put the UI location before the action.
- Use **bold** for UI elements and `code` for things to type.
- Show the **expected result** after important steps.
- Mark dangerous steps: `⚠️ This deletes all data in the database.`

## Tables

Use tables for **comparisons, options, parameters and mappings**. Don't use them for narrative.

- Keep cells short (a few words or one sentence).
- The first column holds the thing being compared.
- Include units in headers: `Timeout (s)`.
- Avoid empty cells. Use `—` for "not applicable".

## Code and commands

````markdown
```bash
php artisan migrate --force
```
````

| Rule | Why |
|---|---|
| Always set the language (`bash`, `json`, `yaml`, `php`, `http`, `sql`, `text`) | Syntax highlighting; tells AI what it is |
| No `$` prompt in copyable commands | Clean copy-paste |
| Show output in a separate `text` block | Readers know what to expect |
| Use realistic, working values | Fake-looking examples confuse |
| Mark placeholders clearly: `<your-api-key>` or `YOUR_API_KEY` | Readers know what to replace |
| Keep examples minimal but complete | Should run as-is |
| Never include real secrets | Use obviously fake values |

Inline code for: file names (`config.yaml`), paths, commands, function/class names, field names, values, env vars.

## Links

- Use descriptive link text: `see the [refund rules](…)`, not `click [here](…)`.
- Use relative paths for internal docs ([markdown-essentials](../foundations/markdown-essentials.md#linking-rules)).
- Link the **first** mention of a concept on a page, not every mention.

## Terminology

- Keep a **glossary** ([example](../foundations/glossary.md)) and use its terms exactly.
- Don't use synonyms for variety: "order" in one paragraph and "purchase" in the next makes readers wonder whether they're different things.
- Match **UI labels** and **code names** exactly, with the same capitalization.
- Prefer common words: "use", not "utilize"; "start", not "initiate".

## Emphasis and callouts

- **Bold** for UI elements and key terms on first use. Don't bold whole sentences.
- *Italic* sparingly, for emphasis or new terms.
- Use callouts (`> [!NOTE]`, `> [!WARNING]`) only for information that genuinely needs attention. If everything is a warning, nothing is.

## Numbers, dates, units

- ISO dates: `2026-10-09`.
- Units with a space: `30 s`, `512 MB`. Be consistent about binary and decimal units.
- Time zones are explicit: `14:00 UTC`.

## Accessibility

- Give images alt text that describes the content, not "image".
- Don't convey meaning by color alone ("the red items").
- Write meaningful link text.
- Use real heading structure, not bold text pretending to be a heading.

---

**Related:** [page-patterns](page-patterns.md) · [markdown-essentials](../foundations/markdown-essentials.md) · [writing-for-ai-agents](writing-for-ai-agents.md)
**Up:** [Writing](README.md)
