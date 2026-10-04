---
name: install-style
description: Copy the bundled STYLE.md writing guide into the current project and point CLAUDE.md at it. Use when the user asks to install, add, or set up the docs style guide.
disable-model-invocation: true
argument-hint: "[destination path, default ./STYLE.md]"
allowed-tools: Bash(cp *) Bash(ls *) Bash(cat *) Bash(diff *) Bash(test *) Read Write Edit
---

Install the writing style guide into the project the user is working in.

The source file is `${CLAUDE_PLUGIN_ROOT}/STYLE.md`. The destination is `$ARGUMENTS` if given, otherwise `STYLE.md` in the project root (`${CLAUDE_PROJECT_DIR}` or the current directory).

Do the following:

1. Check whether the destination already exists.
   - If it does not exist, copy the source there.
   - If it exists and is identical to the source, report that and skip the copy.
   - If it exists and differs, show the user a short `diff` summary and ask whether to overwrite, keep theirs, or write the new file beside it as `STYLE.new.md`. Do not overwrite without an answer.
2. Point the project's `CLAUDE.md` at the guide.
   - If `CLAUDE.md` exists in the project root and does not already mention the destination file, append the block below.
   - If `CLAUDE.md` does not exist, create it with only the block below and say so in the report.
   - If it already mentions the file, leave it alone.

   ```markdown

   ## Writing style

   Follow `STYLE.md` for all explanatory prose: docs, README files, runbooks,
   PR descriptions, long comments, and answers that explain how a system works.
   Read it before writing more than a paragraph.
   ```

   Replace `STYLE.md` in the block with the actual destination path if it differs.
3. Report what was written, what was skipped, and why, in three lines or fewer.

Do not edit any other file. Do not commit.
