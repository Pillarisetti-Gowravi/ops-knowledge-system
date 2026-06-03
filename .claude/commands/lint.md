---
description: Run a health check on the wiki and report findings.
argument-hint: "[optional: focus area, e.g. 'concepts' or 'people']"
---

You are operating inside a second-brain vault. Run a health check on `wiki/` and produce a structured report. Do not fix anything — report only, then ask for permission before touching any file.

If $ARGUMENTS is provided, focus the scan on that subfolder or area. Otherwise scan the entire `wiki/` directory.

## Checks to run

### 1. Broken wiki-links
Scan every `.md` file in `wiki/` for `[[link]]` references. For each link, check whether a file with that name exists somewhere in `wiki/`. Report every link that resolves to no file.

### 2. Orphan pages
List every page in `wiki/` (excluding `index.md` and `log.md`) that is not linked to from any other wiki page. These are pages that exist but cannot be discovered by following links.

### 3. Missing or incomplete frontmatter
Every wiki page must have all six required frontmatter fields: `title`, `type`, `sources`, `related`, `created`, `last-updated`. Report every page missing one or more of these fields. Also flag any page whose `type` value is not one of: `concept`, `entity`, `source-summary`, `comparison`, `project`, `person`.

### 4. Stale pages
Report every wiki page whose `last-updated` date is 30 or more days before today. These may need revisiting.

### 5. Index drift
Compare the pages listed in `wiki/index.md` against the files that actually exist in `wiki/`. Report:
- Pages that exist in the index but whose file cannot be found (dead index entries)
- Pages whose file exists but are not listed in the index (index gaps)

### 6. Contradictions
Look for pages that make explicitly contradictory factual claims about the same topic. Flag any pairs you find with a brief description of the conflict.

## Output format

Return findings as a structured report using this layout:

```
## Wiki Health Report — [today's date]

### Broken Links ([count])
- [[link-name]] in wiki/path/to/page.md

### Orphan Pages ([count])
- wiki/path/to/page.md

### Missing Frontmatter ([count])
- wiki/path/to/page.md — missing: [field names]

### Stale Pages ([count])
- wiki/path/to/page.md — last updated: [date]

### Index Drift
**Dead index entries ([count]):** ...
**Index gaps ([count]):** ...

### Contradictions ([count])
- [[page-a]] vs [[page-b]]: [brief description]

### Summary
[2–3 sentences: overall health, most urgent issues]
```

After delivering the report, ask: "Would you like me to fix any of these? If so, which categories?"
