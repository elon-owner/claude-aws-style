# STYLE.md

This guide describes how to write explanatory text so that a reader can act on it the first time they read it. It applies to README files, reference pages, runbooks, design notes, pull request descriptions, code comments longer than one line, and chat answers that explain how a system works.

The patterns come from a study of about sixty pages of AWS service documentation across six services. Only the patterns were kept. No product facts, names, or example sentences from those pages appear here.

**Contents**

- The ten rules
- Opening a page or section
- Sentences
- Terms and names
- Structure
- Callouts
- Procedures
- Commands, code, and output
- Limits, pricing, and caveats
- Cross-references
- Words and phrases to avoid
- Checklist
- Local adaptations

## The ten rules

1. Open with a one-sentence definition of the thing the page is named after.
2. Write one idea per sentence, in present tense and active voice, 12 to 25 words.
3. "You" is the reader. "We" is the team that owns the system, and appears only for recommendations and for things the team does.
4. Define a term once, in italics, in the sentence where it first appears. Then repeat the exact term. Never vary it.
5. Expand every acronym once, with the acronym in parentheses, then use the acronym.
6. Put the condition first and the consequence second: "If X, Y."
7. State limits as plain numbers. State unsupported behavior as "You can't X." Put the workaround in the same bullet.
8. Write procedures under a bold "To do X" heading, as numbered steps, one action per step.
9. Introduce every link with "For more information, see Title." where Title is the exact title of the target.
10. No marketing adjectives, no hedging, no humor, no exclamation marks, no rhetorical questions.

## Opening a page or section

A page has no preamble. It does not say who it is for, what the reader will learn, or why the feature exists. The first sentence does the work.

**Pattern A, definition.** Use this for a concept or a component.

> A *retry policy* is a set of rules that determines when a failed job runs again. Each queue has exactly one retry policy. You can change the retry policy of a queue at any time.

The three sentences do three jobs. The first defines the term and italicizes it. The second states the key property or the reader's relationship to it. The third begins with "You can" and says what the reader does with it.

**Pattern B, capability.** Use this for a feature the reader turns on or uses.

> You can use job tags to route jobs to specific workers. A worker only takes jobs whose tags match its own.

**Pattern C, hub.** Use this for a page whose only job is to route the reader to child pages.

> The following topics describe how to create, scale, and delete a worker pool.

Follow the sentence with a bulleted list of links.

**Pattern D, reference.** Use this for a page that is mostly a table.

> The following table lists the default quotas for each account. Unless stated otherwise, each quota applies per region.

Reuse an opening verbatim across related pages rather than rephrasing it. A reader who sees the same sentence twice learns that the two pages are siblings.

## Sentences

- Keep sentences between 12 and 25 words. Split anything longer.
- One idea per sentence. Start a new sentence instead of joining two clauses.
- Present tense for everything the system does now, including consequences that happen later. "The worker stops taking jobs as soon as it is drained." Not "will stop".
- Active voice with a concrete subject: the reader, the component, or the team. Passive voice is acceptable only when the actor is the system and naming it adds nothing: "Updates are applied during the maintenance window."
- Condition first: "If the queue has no workers, jobs wait indefinitely." Not "Jobs wait indefinitely if the queue has no workers."
- Imperatives appear in two places only: numbered procedure steps, and explicit advice. Conceptual prose uses "you can" and "you must" instead of bare commands.
- Plain connectives: Therefore, However, Otherwise, That is, For example, Because. Nothing fancier.
- A claim followed by a restatement is a common and useful shape: "Jobs are durable. That is, a job survives a restart of the worker that was running it."
- Contractions are fine: can't, doesn't, isn't, you're.
- Use "might" only for real nondeterminism. "The first request after a deploy might take longer." Never use it to soften a fact you know.

## Terms and names

- Introduce a term in italics in its defining sentence. After that, never italicize it again and never swap in a synonym. If the system has two names for a thing, say so once: "These are called *read nodes*. The console labels them **Replicas**."
- Expand an acronym on first use in each page, even a common one: "Transport Layer Security (TLS)". Then use the short form.
- Generic nouns stay lowercase: worker, queue, retry policy, route table. Product and feature names are capitalized as proper nouns and used in full on first mention.
- Pick one spelling for every compound noun and keep it: "job ID", not "job id" or "Job Id".
- Identifiers, states, parameter names, file names, and values go in code font: `running`, `max_retries`, `us-east-1`.
- Labels that appear in a user interface go in bold, exactly as the interface spells them: choose **Save changes**.
- Command names and API operations go in code font and keep the casing of the tool: `create-queue` for a CLI, `CreateQueue` for an API.
- When a code-font name and a bold UI label refer to the same thing, say so: "The `health_check_path` attribute is labeled **Health check path** in the console."

## Structure

**Page shape.** Title, one to three opening paragraphs, a bold **Topics** or **Contents** list of links, then sections. Long sections may carry their own **Contents** list.

**Headings.** Noun phrases for concepts ("Retry policies"), gerunds for tasks ("Creating a worker pool"), and no questions except a single top-level "What is X?". Headings are sentence case.

**Prose or list.** Prose explains behavior. A bulleted list collects three or more parallel facts. Each bullet is a complete sentence with a terminal period. A bullet that introduces a named item starts with the name in bold, followed by a colon or a period, then the description.

**Grouped lists.** Caveats and conditions live under a bold run-in label, not scattered through the prose: **Considerations**, **Requirements**, **Limitations**, **Prerequisites**, **Best practices**, **Next steps**.

**Tables.** Use a table for anything comparative or numeric: settings, ranges, quotas, feature support. Introduce every table with one sentence: "The following table lists the settings for a health check." For a comparison table, put the characteristic in the first column and one column per thing compared. Cells are fragments, not sentences.

**Definition lists.** For a catalog of attributes or fields, put the term on its own line and the description indented beneath it.

**Images and diagrams.** Introduce each one: "The following diagram shows the states a job moves through." Give it descriptive alt text.

## Callouts

Callouts are rare and graded. Most pages have one or none. Put the label in bold on its own line.

| Label | Use it for | Example |
|---|---|---|
| **Tip** | An optional convenience the reader might not know about. | A shortcut in the console, a shorter command form. |
| **Note** | A side fact or a scope qualification that does not change the main path. | "This section covers only queues created after the migration." |
| **Important** | Something that fails, costs money, or cannot be undone if the reader ignores it. | "You can't view the generated password again after you close this dialog." |
| **Warning** | Data loss or a destructive outcome. | "Deleting a pool erases every job that has not been acknowledged." |

A caveat that is not urgent does not get a callout. It goes in a **Considerations** list.

## Procedures

A procedure page has four parts in this order: a one-sentence context paragraph, **Prerequisites** if any, the procedure itself, and **Next steps**.

When a task can be done with more than one tool, give each tool its own section in a fixed order (for example: console, CLI, API), each with its own "To do X" heading. Do not mix tools in one numbered list.

**The heading.** Bold, infinitive form, names the goal and the tool: **To create a worker pool using the console**.

**The steps.**

1. Number every step. One action per step.
2. Make the first step identical on every page that uses the same tool: "Open the console at URL." A reader should recognize it instantly.
3. Use a fixed verb for each kind of control. "Choose" for buttons, menu items, and links. "Select" for list rows, radio buttons, and check boxes. "Enter" for text. "Clear" for a check box. "Expand" for a collapsed section.
4. Name a form field with "For **Field**, choose X." or "For **Field**, enter X."
5. Prefix optional steps with "(Optional)".
6. Put explanatory text under the step, as its own paragraph, not inside the step sentence.
7. State expected waits inline: "It can take a few minutes for the pool to become `active`."
8. Nest sub-steps under a step that ends with "do the following:".

**The command-line form.** Not numbered. One sentence that names the command, then one code block with placeholders, then the output.

> Use the `create-pool` command.
>
> ```
> tool create-pool --name my-pool --size 3
> ```
>
> The following is example output.

**The API form.** Mirrors the command-line section with the operation and parameter names in the API's casing. Usually no code block.

## Commands, code, and output

- Introduce every code block with a sentence that ends in a colon or says what the block is: "Use the following query to list stuck jobs:" or "The following is example output."
- Show placeholders in a visually distinct way and use the same placeholder convention throughout the document.
- When a command differs by shell or platform, give each variant under its own one-line label: "For Linux, macOS, or Unix:" and "For Windows:".
- After a command that produces output, show the output or describe what the reader should see: "You should see output similar to the following."
- Never put a command, a parameter name, or an identifier in prose without code font.

## Limits, pricing, and caveats

- State a limit as a plain number in the sentence that defines the setting, with the range and the default together: "The range is 2 to 120 seconds. The default is 5 seconds."
- Label a hard limit as a hard limit: "The following limits cannot be changed."
- A quota table has four columns: Name, Default, Adjustable, Comments. Side effects of raising a quota go in Comments.
- State unsupported behavior flatly, as a complete sentence, with no apology: "You can't attach a pool to more than one queue." "Health checks do not support WebSockets."
- Put the workaround in the same bullet as the restriction: "You can't turn off encryption on an encrypted volume. However, you can restore an unencrypted copy from a snapshot."
- Say what fails and how: "After the quota is reached, further create calls fail with an exception."
- Never quote a price. State the billing rule qualitatively and precisely, then link to the price list: "You are charged for provisioned capacity whether or not you use it. For more information, see Pricing."
- Gate features on exact versions: "Available in version 2.9.1 and higher." Not "recent versions".
- Note cost side effects where they arise, not in a separate section: "There is no charge for the gateway itself. Data transfer through it is charged at the standard rate."
- Name a deprecated feature as deprecated, with a date. Do not quietly remove it.

## Cross-references

- One formula: "For more information, see Title." Title is the exact title of the target page, so the reader can predict what they will find.
- Narrower variants: "For more information about X, see Title." "For examples, see Title." "To get started, see Title."
- When the target is in another guide or repository, append the source in italics: "see Rotating keys in the *Platform Security Guide*."
- Place the link sentence at the end of the paragraph it supports. Inline links on a noun are acceptable only on the first mention of a key term.
- Never write "click here", "this page", "check out", or "learn more" as link text.
- Do not restate a definition that exists on a linked page. Link to it.
- Introduce a list of related pages with "For more information, see the following documentation:".

## Words and phrases to avoid

| Avoid | Use instead |
|---|---|
| simply, just, easy, easily | Delete the word. |
| powerful, seamless, robust, best-in-class | Delete the adjective, or state the mechanism that makes it so. |
| please | Delete the word. |
| In this section you will learn | Delete the sentence. Start with the definition. |
| will (for current behavior) | Present tense. |
| may want to consider | A direct recommendation: "We recommend X." Or a condition: "If Y, use X." |
| generally, usually, in most cases (unqualified) | The concrete condition under which the statement holds. |
| as we will see below, as mentioned above | Delete, or link to the section by title. |
| is not supported at this time | "isn't supported." |
| click | "choose" |
| Exclamation marks, rhetorical questions, emoji | Delete. |
| Bold for emphasis in prose | Plain text. Bold is reserved for UI labels and run-in list labels. |
| I, my | Rewrite with "you" or with the component as subject. |
| A paragraph on why the feature exists | One clause at most, attached to the definition. |
| An apology for complexity | Delete. |

## Checklist

Before publishing, confirm each item.

- The first sentence defines the subject or states what the reader can do.
- No sentence is longer than 25 words.
- Every new term is italicized once and then repeated without variation.
- Every acronym is expanded on first use.
- Every table and code block has an introducing sentence.
- Every procedure has a bold "To do X" heading, numbered steps, and one action per step.
- Every limit is a number. Every unsupported behavior is a "You can't" sentence.
- Every link reads "For more information, see Title."
- No callout is used where a **Considerations** bullet would do.
- No word from the avoid table remains.

## Local adaptations

The source documentation separates a bold list term from its description with a spaced dash. This guide uses a colon or a period instead, because many house styles forbid dashes in prose.

Where this guide conflicts with a repository's own CLAUDE.md or contributor guide, the repository wins. Add the conflicting rule to this section so the next writer sees it.
