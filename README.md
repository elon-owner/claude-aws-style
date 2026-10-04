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

Clone the repository, start Claude Code with the plugin directory, and run the install skill inside your project:

```
git clone git@github.com:elon-owner/claude-aws-style.git
claude --plugin-dir ./claude-aws-style
/install-style
```

Run the second command from the project that should receive the guide, and adjust the path to wherever you cloned the repository.

The `--plugin-dir` flag loads the plugin for that session only. To load it every time, add the flag to a shell alias, or add the repository to a plugin marketplace and install it with `/plugin install aws-docs-style@<marketplace>`.

To check the plugin before loading it:

```
claude plugin validate ./claude-aws-style
```

## What `/install-style` does

It copies `STYLE.md` to the project root and appends a short "Writing style" section to the project's `CLAUDE.md`. If a `STYLE.md` already exists and differs, the skill shows a diff and asks before overwriting. Pass a path to install somewhere else: `/install-style docs/STYLE.md`.

## License

MIT
