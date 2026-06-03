# 🧠 Ops Knowledge System

> An AI-powered knowledge system for operational teams — built with Obsidian + Claude Code.

Stop losing decisions in Slack threads. Stop re-reading meeting notes nobody documented. Stop onboarding people into chaos.

This system gives your ops team one place where everything lives, everything links, and Claude does the organizing for you.

---

## 🎯 Who This Is For

- Logistics and supply chain teams
- Warehouse and fleet managers
- Startup founders and ops leads
- Anyone drowning in Slack, email, and scattered meeting notes

---

## 🛠️ What You Need

| Tool | Cost | Purpose |
|---|---|---|
| [Obsidian](https://obsidian.md) | Free | Visual workspace and markdown editor |
| [Claude Code](https://claude.ai/code) | Anthropic subscription | AI agent that manages your wiki |
| [Obsidian Git Plugin](https://github.com/denolehov/obsidian-git) | Free | Auto-syncs vault to GitHub every 10 min |
| [Obsidian Web Clipper](https://obsidian.md/clipper) | Free | Capture articles directly into raw/ |

---

## 📁 Vault Structure

```
ops-knowledge-system/
├── raw/                        # Your source material — Claude never edits this
│   ├── claude-exports/         # Conversation exports from Claude.ai
│   ├── notion-exports/         # Page exports from Notion
│   ├── granola-exports/        # Meeting note exports from Granola
│   ├── articles/               # Saved articles and web clips
│   └── notes/                  # Freeform personal notes
│
├── wiki/                       # Claude's domain — all pages built and maintained here
│   ├── index.md                # Master catalog of every wiki page
│   ├── log.md                  # Append-only log of every change Claude makes
│   ├── concepts/               # Ideas, frameworks, domain knowledge
│   ├── projects/               # Project pages — goals, status, decisions
│   └── people/                 # People dossiers — context, key exchanges
│
├── journal/                    # Daily notes — yours, not Claude's
├── content/                    # Drafts, outlines, published pieces
├── priorities.md               # Your steering wheel — update weekly
└── CLAUDE.md                   # Claude's identity and rules for your vault
```

### The Core Rule
**`raw/` is read-only.** Claude reads it, never edits it.
**`wiki/` is Claude's.** You don't need to write here — Claude does it for you.

---

## ⚡ Slash Commands

These live in `.claude/commands/` and give you control of the entire system.

| Command | What It Does |
|---|---|
| `/ingest` | Reads raw/ files and compiles them into structured wiki pages |
| `/briefing` | Morning command — scans calendar, logs, wiki → gives you a focused daily plan |
| `/debrief` | Evening command — you tell Claude what happened, it updates the wiki |
| `/query` | Ask any question, get an answer cited from your own data |
| `/lint` | Health check — catches broken links, missing metadata, incomplete pages |
| `/log` | Quick capture — appends a timestamped note to wiki/log.md |

---

## 🔄 The Daily Loop

```
Morning                          Evening
────────                         ───────
/briefing                        /debrief
    │                                │
    ▼                                ▼
Scan calendar              Tell Claude what happened
Scan wiki                  Claude updates wiki pages
Scan priorities            Claude flags action items
    │                      Claude shifts priorities
    ▼                                │
One focused plan                     ▼
for today               Knowledge compounds overnight
```

---

## 🚀 Setup Guide

### Step 1 — Install Obsidian
Download from [obsidian.md](https://obsidian.md) and create a new vault on your local machine.

### Step 2 — Create the folder structure
Inside your vault, create these folders manually:
```
raw/  wiki/  journal/  content/
```
Inside `raw/`, create subfolders: `claude-exports/  notion-exports/  granola-exports/  articles/  notes/`

Inside `wiki/`, create: `concepts/  projects/  people/` and two files: `index.md` and `log.md`

### Step 3 — Add CLAUDE.md
Copy the `CLAUDE.md` from this repo into your vault root. Edit the **Domain Context** section to reflect your business, your industry, and your key people.

### Step 4 — Add slash commands
Copy the `.claude/commands/` folder from this repo into your vault. These are the commands Claude will run when you type `/briefing`, `/ingest`, etc.

### Step 5 — Add priorities.md
Copy `priorities.md` from this repo and update it with your real projects, areas, and key people. This is your steering wheel — Claude reads it at the start of every briefing.

### Step 6 — Drop your data into raw/
Export your notes from Notion, Claude.ai, or wherever you work. Drop them into the relevant `raw/` subfolder.

### Step 7 — Run your first ingest
Open Claude Code in your vault directory and run:
```
/ingest
```
Claude will read your raw files and build your first wiki pages. Open Obsidian's Graph View to see everything connect.

### Step 8 — Set up GitHub backup (optional but recommended)
1. Create a private GitHub repo
2. Install the Obsidian Git plugin
3. Configure it to auto-commit every 10 minutes
4. Your brain is now backed up and accessible from any machine

---

## 🗂️ Demo Files

The `demo/` folder contains sample files so you can see exactly what the system produces:

- `demo/raw/sample-meeting-note.md` — what a raw input looks like
- `demo/wiki/project-management/metro-freight-launch.md` — what Claude builds from it
- `demo/wiki/index.md` — the master catalog structure

---

## 💡 Real Use Cases for Ops Teams

**Dispatchers**
Run `/debrief` after shift handoff. Every route change, driver note, and client issue is documented and searchable — not lost in a radio log.

**Warehouse Managers**
Drop vendor emails and meeting notes into `raw/`. Claude builds a vendor page that tracks on-time rates, contract dates, and open issues automatically.

**Founders and Ops Leads**
Run `/briefing` every morning. Claude surfaces your highest-priority items, open action items from yesterday's calls, and what's at risk — before you open Slack.

---

## 🙏 Credits

- **[NextWork](https://www.nextwork.org)** — methodology and inspiration for this system
- **[Anthropic](https://www.anthropic.com)** — Claude Code, the AI agent powering the wiki
- **[Andrej Karpathy](https://twitter.com/karpathy)** — vision behind AI-powered personal knowledge systems
- **[Obsidian](https://obsidian.md)** — the best local-first knowledge workspace available

---

## 📬 Questions?

Built and maintained by [Gowravi Pillarisetti](https://www.linkedin.com/in/pillarisetti-gowravi)

Drop a comment on the LinkedIn post or DM me — happy to walk you through setup.
