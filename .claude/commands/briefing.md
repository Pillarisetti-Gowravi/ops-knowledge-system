Read `priorities.md` from the vault root. Then read the last 3 entries from `wiki/log.md`. Then read any wiki pages under `wiki/projects/` that correspond to active projects listed in priorities.md (skip anything in the Archive section). Finally, produce a briefing with the following structure:

---

## Today's Active Threads

List each active project from priorities.md with a one-line status drawn from the corresponding wiki/projects/ page (if it exists). If no wiki page exists yet, note that.

## Priority Reminders

Pull the 3 most time-sensitive or highest-stakes items from priorities.md — things with target dates, blockers, or explicit urgency signals. Quote or paraphrase directly from the file; do not invent details.

## Suggested Actions

Based on the active threads and the last 3 log entries, suggest 3–5 concrete next steps. Each suggestion should be one sentence, actionable, and tied to a specific project or area. Prefer actions that unblock progress or close a known gap.

---

After generating the briefing, append a new row to `wiki/log.md` in this exact format:
`| YYYY-MM-DD | briefing | wiki/log.md | priorities.md, wiki/log.md |`

Use today's date. Do not modify any other file.
