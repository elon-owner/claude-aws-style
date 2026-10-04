---
name: docs-style
description: Apply the reference-documentation writing style (definition-first openings, one idea per sentence, terms defined once in italics, acronyms expanded, graded callouts, numbered "To do X" procedures, flat statements of limits) when writing or rewriting README files, docs, runbooks, design notes, PR descriptions, or any explanatory prose longer than a paragraph. Also use when the user asks to rewrite a file in the docs style.
argument-hint: "[file to rewrite]"
---

Write or rewrite explanatory prose so that a reader can act on it the first time.

Load the guide first:

1. If the project has a `STYLE.md` in its root, read that. It is the project's adapted copy and takes precedence.
2. Otherwise read `${CLAUDE_PLUGIN_ROOT}/STYLE.md`.

Then apply it. The rules that matter most, in order:

- The first sentence defines the subject ("A *term* is a category that does X.") or states the capability ("You can use X to Y."). No preamble, no audience statement, no "in this document you will learn".
- One idea per sentence, 12 to 25 words, present tense, active voice, condition before consequence.
- "You" is the reader. "We" is the owning team and appears only in "We recommend" or for things the team does.
- Define each term once in italics, then repeat it exactly. Expand each acronym once.
- Three or more parallel facts become a bulleted list. Anything comparative or numeric becomes a table with an introducing sentence.
- Caveats go under a bold **Considerations** or **Limitations** label as "You can't X. However, you can Y." sentences. Callouts are reserved: **Note** for scope, **Important** for cost or irreversibility, **Warning** for data loss.
- Procedures get a bold "To do X" heading and numbered steps with one action each.
- Links read "For more information, see Title."
- Delete every word in the guide's avoid table.

If `$ARGUMENTS` names a file, rewrite that file in place. Preserve every fact, number, name, and link in the original. Change only wording, order, and structure. After writing, list the three largest changes you made in one line each.

If no file is named, apply the guide to whatever you are about to write in this turn.

Respect the repository's own CLAUDE.md where it conflicts with the guide. In particular, if the repository forbids dashes or semicolons, do not introduce them.
