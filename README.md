# aws-docs-style

A Claude Code plugin that installs a `STYLE.md` writing guide into your project. The guide captures how AWS service documentation achieves clarity: definition-first openings, one idea per sentence, terms defined once, graded callouts, numbered procedures, and flat statements of limits. It holds patterns only. No product facts from the source pages are retained.

## What the plugin contains

| Path | Purpose |
|---|---|
| `STYLE.md` | The writing guide. Service-agnostic. About 250 lines. |
| `skills/install-style` | `/install-style [path]` copies the guide into your project and points `CLAUDE.md` at it. User-invoked only. |
| `skills/docs-style` | `/docs-style [file]` rewrites a file in the style, or applies the style to whatever Claude is about to write. Claude also loads it on its own when writing docs. |
| `skills/review-docs-style` | `/review-docs-style <file>` reports violations with line numbers and suggested rewrites. Read-only. |

## Installing the plugin

**For one session.** Run Claude Code with the plugin directory:

```
claude --plugin-dir /path/to/aws-docs-style
```

**Validate first.**

```
claude plugin validate /path/to/aws-docs-style
```

**From a marketplace.** Add an entry to a marketplace `marketplace.json` whose `source` points at this directory, then install with `/plugin install aws-docs-style@<marketplace>`.

## Installing the guide into a project

After the plugin is loaded, open the project and run:

```
/install-style
```

This copies `STYLE.md` to the project root and appends a short "Writing style" section to the project's `CLAUDE.md`. If a `STYLE.md` already exists and differs, the skill shows a diff and asks before overwriting. Pass a path to install somewhere else: `/install-style docs/STYLE.md`.

## How the guide was built

Six research agents each read ten pages of AWS documentation, five overview pages and five capability pages, for EC2, Application Load Balancer, Aurora, Aurora PostgreSQL, VPC, and RDS. Each agent reported on openings, sentence structure, terminology, page structure, callouts, procedures, limits and pricing, cross-references, and what the pages avoid. The reports agreed on nearly every point. `STYLE.md` is the intersection.

One deliberate change: the source pages separate a bold list term from its description with a spaced dash. The guide uses a colon or a period instead, because many house styles forbid dashes in prose.

## License

MIT
