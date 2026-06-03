# CLAUDE.md — Second Brain Vault

Instructions for Claude when working inside this vault.

---

## 1. Project Structure

This vault has a strict separation between source material (yours) and synthesized knowledge (mine).

```

├── raw/                    # Your source documents — NEVER modified by Claude
│   ├── claude-exports/     # Conversation exports from Claude.ai
│   ├── chatgpt-exports/    # Conversation exports from ChatGPT
│   ├── notion-exports/     # Page and database exports from Notion
│   ├── granola-exports/    # Meeting note exports from Granola
│   ├── articles/           # Saved articles, PDFs, web clips
│   └── notes/              # Freeform personal notes and quick captures
├── wiki/                   # Claude's domain — all pages created and maintained here
│   ├── index.md            # Master catalog: every wiki page listed and linked
│   ├── log.md              # Append-only activity log of every change Claude makes
│   ├── concepts/           # Concept and topic pages (ideas, frameworks, domains)
│   ├── projects/           # Project-specific pages (goals, status, decisions)
│   └── people/             # People dossiers (context, key exchanges, links)
├── journal/                # Daily notes — written by the user, owned by the user
├── content/                # Content pipeline (drafts, outlines, published pieces)
└── priorities.md           # User-maintained priorities (read at start of /briefing and /debrief)
```

### Key rules

- `raw/` is **read-only**. Claude reads these files but never edits, moves, or deletes them.
- `wiki/` is **Claude's write domain**. The user should not need to edit wiki pages directly.
- `wiki/index.md` must be updated whenever a page is created or its title changes.
- `wiki/log.md` must receive an append-only entry for every change Claude makes to the wiki. Format: `| YYYY-MM-DD | action | files affected | source(s) used |`
- `journal/` and `content/` belong to the user. Claude may read them as sources but should not write to them unless explicitly asked.
- `priorities.md` is the user's priorities file at the vault root. It contains Projects (short-term deliverables with target dates), Areas (ongoing responsibilities), Resources (topics for reference), Archive (completed or paused items), and Key People. Read this file at the start of every /briefing and /debrief. Prioritise signals tied to Projects and Areas; use Resources for background context; skip anything in Archive.

---

## 2. Page Conventions

### Frontmatter

Every wiki page must open with YAML frontmatter containing these fields:

```yaml
---
title: "Page Title"
type: concept           # one of: concept | entity | source-summary | comparison | project | person
sources:
  - raw/notes/YYYY-MM-DD-example.md
related:
  - "[[another-page]]"
created: YYYY-MM-DD
last-updated: YYYY-MM-DD
---
```

- `type` must be one of the six values above — do not invent new types.
- `sources` lists every `raw/` file that contributed to this page. Use relative paths from the vault root.
- `related` uses `[[wiki-link]]` syntax pointing to other wiki pages.
- `last-updated` must be refreshed every time the page is edited.

### Linking

- Use `[[page-name]]` wiki-link syntax for all internal references.
- Link liberally — if a concept, person, or project mentioned on a page has its own wiki page, link to it.
- Do not invent links to pages that do not yet exist, but do note when a page *should* exist and hasn't been created.

### Atomicity

Each page covers **one idea, one person, or one project**. If a page is trying to cover two distinct things, split it. The index exists precisely so that many small, focused pages remain navigable.

### Heading structure

```
# Title                  ← matches `title` in frontmatter, H1 only once
## Summary               ← 2–4 sentence synthesis, always first
## [Content sections]    ← varies by page type (see below)
## Sources               ← bulleted list of raw/ files, with one-line description each
## Open Questions        ← optional; unresolved things worth revisiting
```

**Per-type content sections:**

| Type | Expected sections |
|------|------------------|
| `concept` | Summary, Definition, How It Appears in My Notes, Related Concepts |
| `entity` | Summary, Context, Key Details, Connections |
| `source-summary` | Summary, Key Points, Notable Quotes, My Take |
| `comparison` | Summary, Side-by-Side, When to Use Which, Sources |
| `project` | Summary, Goal, Status, Key Decisions, Open Questions, People Involved |
| `person` | Summary, Role / Relationship, Context, Notable Exchanges |

---

## 3. Style Guide

- **Prose:** Clear and concise. Write as if explaining to a well-informed version of the user who has forgotten the details.
- **Lists over paragraphs:** Prefer bullet points when enumerating facts, decisions, or attributes. Reserve paragraphs for synthesis and explanation.
- **Attribution:** Every factual claim must be traceable to a source. If a claim comes from `raw/notes/2026-05-30-meeting.md`, say so — either inline or in the Sources section.
- **Contradictions:** If two sources say different things, note the contradiction explicitly rather than silently picking one. Use this pattern:
  > **Contradiction:** [source A] says X; [source B] says Y. Unresolved.
- **Neutral voice:** Summarize and synthesize; do not editorialize beyond flagging open questions.
- **No invented details:** If a source is ambiguous, say so. Never fill gaps with plausible-sounding information.
- **Tense:** Use present tense for concepts and enduring facts. Use past tense for events and decisions that occurred at a specific time.

---

## 4. Domain Context

This second brain belongs to an AI operations strategist and builder focused on AI adoption in traditional industries — supply chain, logistics, construction, and real estate — not AI for its own sake, but AI that solves real workflow problems that real people face every day. The core orbit is operational intelligence: building signal-based GTM systems, workflow automations, and AI agents that connect business problems with practical solutions using tools like Claude, n8n, LangGraph, Python, and SQL. The knowledge gaps being actively closed include GTM engineering execution (closing the gap between knowing what a system should do and being able to build and run one end to end), sales and outreach confidence (cold calling, discovery, handling objections), and deeper operational fluency in how dispatchers, warehouse managers, and construction ops people actually think and make decisions on the ground. A recurring goal is learning how successful startups validate problems, build solutions, gain customers, and scale adoption — and applying those lessons to AI-first products in operational software. Most importantly, this vault exists to connect ideas, lessons, conversations, projects, and industry insights over time — to link quotes, philosophies, past decisions, and hard-won lessons to each other so that patterns become visible, past mistakes are not repeated, and scattered learning compounds into clear execution and long-term expertise. When processing sources, prioritize surfacing connections across notes, flagging repeated themes, and explicitly linking new material to existing wiki pages wherever relevant.
