---
description: Ingest new files from raw/ into wiki/.
argument-hint: "[number of sources to process, default 5–10]"
---

You are operating inside a second-brain vault. Your job is to ingest unread source files from `raw/` and build or update pages in `wiki/`.

## What counts as "unread"

A file in `raw/` is considered already summarised if a page exists in `wiki/` whose frontmatter `sources` field lists that file path. Skip those files. Process only files not yet referenced in any wiki page's `sources`.

## How many to process

If $ARGUMENTS is provided, process exactly that many source files. Otherwise process 5–10, choosing the most recently modified first.

## For each source file

Work through the following steps in order:

1. **Read the source file** in full. Identify the main topics, people, projects, decisions, and insights it contains.

2. **Write a source-summary page** at `wiki/source-summaries/YYYY-MM-DD-filename.md` (create the subfolder if it does not exist). Use this structure:
   ```
   ---
   title: "Summary: [descriptive title]"
   type: source-summary
   sources:
     - [path to the raw file]
   related: []
   created: [today's date]
   last-updated: [today's date]
   ---
   ## Summary
   ## Key Points
   ## Notable Quotes
   ## My Take
   ## Open Questions
   ```

3. **Create or update concept pages** in `wiki/concepts/` for every significant idea or framework the source introduces or develops. If a concept page already exists, add new information from this source rather than overwriting it. Update `last-updated` and add the source to the `sources` list.

4. **Create or update project pages** in `wiki/projects/` for any project mentioned. Same merge rule — add, don't overwrite.

5. **Create or update person pages** in `wiki/people/` for any person mentioned with enough context to warrant a dossier entry.

6. **Cross-link everything** using `[[wiki-link]]` syntax. Every new or updated page should link to every other relevant page it references. Link the source-summary page to all concept/project/person pages it produced, and vice versa.

7. **Update `wiki/index.md`** — add every newly created page under the correct section (Concepts, Projects, People, Source Summaries). Do not remove existing entries.

8. **Append to `wiki/log.md`** a single table row per file processed:
   `| [today's date] | ingested | [list of files written or updated] | [raw source path] |`

## Constraints

- Never edit or delete any file in `raw/`.
- Never invent facts not present in the source. If something is ambiguous, say so on the page.
- If two sources contradict each other on a concept page, note the contradiction explicitly: **Contradiction:** [source A] says X; [source B] says Y. Unresolved.
- After processing all sources for this run, print a short summary: how many files ingested, how many pages created, how many updated.
