---
description: Synthesise an answer from the wiki.
argument-hint: "the question to answer"
---

You are operating inside a second-brain vault. Your job is to answer a question by synthesising what the wiki already knows.

The question is: $ARGUMENTS

## Step 1 — Orient

Read `wiki/index.md` to get a full picture of what pages exist. Identify every page that is likely to be relevant to the question.

## Step 2 — Read

Read each relevant page in full. Prioritise pages in `wiki/concepts/`, `wiki/projects/`, and `wiki/people/`. Also read any source-summary pages that those pages link to if the question requires going deeper.

## Step 3 — Synthesise

Write a clear, direct answer to the question. Follow these rules:

- **Ground every claim in the wiki.** After each claim, cite the wiki page it comes from in parentheses, e.g. *(→ [[page-name]])*.
- **Integrate across pages.** The best answers connect ideas from multiple pages. Do not just summarise one page.
- **Flag disagreements.** If two wiki pages say different things about the same point, note the conflict explicitly rather than picking one silently: *Conflict: [[page-a]] says X; [[page-b]] says Y.*
- **Flag gaps.** If the wiki does not have enough information to answer part of the question, say so clearly. Suggest which `raw/` sources (if any) might fill the gap and could be ingested with `/ingest`.

## Step 4 — Propose updates (do not write)

If synthesising the answer revealed a connection or insight that is not yet captured in the wiki — a link between two concepts, a pattern across projects, a gap that should become a page — propose the update in a clearly labelled section at the end:

```
## Proposed Wiki Updates
- [ ] [description of proposed change or new page] — reason: [why this insight belongs in the wiki]
```

Do not write any of these updates until the user explicitly confirms.
