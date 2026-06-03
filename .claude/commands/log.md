---
description: Append a timestamped note to wiki/log.md.
argument-hint: "the thought or note to capture"
---

You are operating inside a second-brain vault. Capture a note and, where possible, connect it to existing wiki pages.

The note to capture is: $ARGUMENTS

## Step 1 — Append to the log

Open `wiki/log.md` and append a new row to the activity table:

`| [today's date] | note | wiki/log.md | (direct entry) |`

Below the table row (or in a notes column if the table has one), include the full text of the note so it is searchable in the log.

## Step 2 — Check for connections

Read `wiki/index.md`. Scan the note for mentions of:
- Any **project** that has a page in `wiki/projects/`
- Any **person** that has a page in `wiki/people/`
- Any **concept** that has a page in `wiki/concepts/`

For each match found, open that page and determine whether the note adds meaningful new information — a new decision, a new insight, a status change, a relevant quote or observation.

## Step 3 — Update matched pages (if warranted)

If the note adds meaningful new information to a matched page:
- Add the relevant content under the appropriate section heading.
- Update the page's `last-updated` frontmatter field to today's date.
- Do not rewrite or restructure the existing page — append and link only.
- Add a `[[log]]` back-reference note if the entry is significant enough to trace.

## Step 4 — Do not create new pages

If the note mentions a project, person, or concept that does not yet have a wiki page, do not create one automatically. Instead, note at the end of your response:

> "No wiki page exists for [X]. Run `/ingest` or ask me to create a page if you want this captured in the wiki."

## Constraints

- Never delete or overwrite existing content in `wiki/log.md`.
- Never create new wiki pages in this command — update only.
- Keep your response short: confirm what was logged and what (if anything) was updated.
