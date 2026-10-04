---
name: review-docs-style
description: Review a document against the STYLE.md writing guide and report violations with line numbers and a suggested rewrite for each. Use when the user asks to check, lint, review, or audit docs or prose for style and clarity.
argument-hint: "<file or glob>"
allowed-tools: Read Bash(ls *) Bash(wc *) Bash(grep *) Bash(find *)
---

Review the file or files named in `$ARGUMENTS` against the writing guide. Do not edit anything.

Load the guide first: the project's root `STYLE.md` if present, otherwise `${CLAUDE_PLUGIN_ROOT}/STYLE.md`.

Check each of these, in this order, and stop collecting after the first 20 findings:

1. **Opening.** Does the first sentence define the subject or state what the reader can do? Flag preambles, audience statements, and motivation paragraphs.
2. **Sentence length and shape.** Flag sentences over 25 words, sentences carrying two ideas, future tense for current behavior, and passive voice with a nameable actor.
3. **Terms.** Flag terms used under two or more names, terms never defined, and acronyms never expanded.
4. **Lists and tables.** Flag three or more parallel facts buried in prose, tables or code blocks with no introducing sentence, and bullets that are fragments where sentences are expected.
5. **Callouts.** Flag a Note, Important, or Warning used for something a **Considerations** bullet would carry, and flag mismatched severity.
6. **Procedures.** Flag unnumbered steps, steps with more than one action, missing "To do X" headings, inconsistent control verbs, and mixed tools in one list.
7. **Limits and caveats.** Flag vague quantities ("recent versions", "a few"), hedged facts, and restrictions with no workaround where one exists.
8. **Links.** Flag "click here", "this page", "learn more", and link text that is not the target's title.
9. **Avoid list.** Flag every word from the guide's avoid table.

Report as a table with four columns: Line, Rule, Finding, Suggested rewrite. Keep each suggested rewrite to one sentence. After the table, give a one-line verdict: ready, needs light edits, or needs restructuring.

If the user also asks you to fix the findings, switch to the `docs-style` skill for the rewrite.
