# 🧠 Ops Knowledge System

> An AI-powered knowledge system for industrial and operational teams — built with Obsidian + Claude Code.

Shift handoff notes that never made it to the next team. Vendor issues raised in a standup that disappeared by Friday. Client onboarding spread across three inboxes. Project decisions made in a hallway — never written down.

This system fixes that. One place where everything lives, everything links, and Claude does the organizing for you.

---

## 🎯 Who This Is For

This is not a tech tool for tech teams. This is built for the industries where operational complexity is highest and documentation is worst:

- **Supply Chain & Logistics** — dispatchers, fleet managers, warehouse ops
- **Construction** — project managers, site supervisors, subcontractor coordination
- **Real Estate** — property managers, transaction coordinators, asset managers
- **Energy & Utilities** — field ops, maintenance scheduling, compliance tracking
- **Finance & Professional Services** — ops leads, client relationship managers, analysts

If your team runs on Slack messages, WhatsApp threads, and meeting notes nobody reads — this is for you.

---

## 🛠️ What You Need

| Tool | Cost | Purpose |
|---|---|---|
| [Obsidian](https://obsidian.md) | Free | Visual workspace and markdown editor |
| [Claude Code](https://claude.ai/code) | Anthropic subscription | AI agent that manages your wiki |
| [Obsidian Git Plugin](https://github.com/denolehov/obsidian-git) | Free | Auto-syncs vault to GitHub every 10 min |
| [Obsidian Web Clipper](https://obsidian.md/clipper) | Free | Capture articles and reports directly into raw/ |

---

## 📁 Vault Structure

```
ops-knowledge-system/
├── raw/                        # Your source material — Claude never edits this
│   ├── meeting-exports/        # Notes from standups, site visits, client calls
│   ├── emails/                 # Key email threads worth documenting
│   ├── reports/                # Industry reports, vendor submissions, audits
│   ├── contracts/              # Contract summaries and renewal dates
│   └── notes/                  # Freeform captures and quick thoughts
│
├── wiki/                       # Claude's domain — all pages built and maintained here
│   ├── index.md                # Master catalog of every wiki page
│   ├── log.md                  # Append-only log of every change Claude makes
│   ├── concepts/               # Domain knowledge, frameworks, industry context
│   ├── projects/               # Project pages — goals, status, key decisions
│   ├── people/                 # Contacts, vendors, clients, team members
│   └── financial-updates/      # Cost summaries, budget tracking, vendor spend
│
├── journal/                    # Daily notes — yours, not Claude's
├── content/                    # Reports, proposals, published documents
├── priorities.md               # Your steering wheel — update weekly
└── CLAUDE.md                   # Claude's identity and operating rules for your vault
```

### The Core Rule
**`raw/` is read-only.** Claude reads it, never edits it.
**`wiki/` is Claude's.** You don't need to write here — Claude does it for you.

---

## ⚡ Slash Commands

These live in `.claude/commands/` and give you full control of the system.

| Command | What It Does |
|---|---|
| `/ingest` | Reads raw/ files and compiles them into structured wiki pages |
| `/briefing` | Morning command — scans calendar, logs, wiki → one focused daily plan |
| `/debrief` | Evening command — you tell Claude what happened, it updates the wiki |
| `/query` | Ask any question, get an answer cited from your own data |
| `/lint` | Health check — catches broken links, missing metadata, incomplete pages |
| `/log` | Quick capture — appends a timestamped note to wiki/log.md |

---

## 🔄 The Daily Operating Loop

```
Morning                              Evening
───────                              ───────
/briefing                            /debrief
    │                                    │
    ▼                                    ▼
Scan calendar                  Tell Claude what happened
Scan wiki                      Claude updates wiki pages
Scan priorities                Claude surfaces action items
    │                          Claude shifts priorities
    ▼                                    │
One focused plan                         ▼
for today                  Knowledge compounds overnight
```

---

## 🚀 Setup Guide

### Step 1 — Install Obsidian
Download from [obsidian.md](https://obsidian.md) and create a new local vault on your machine.

### Step 2 — Create the folder structure
Inside your vault, create these top-level folders:
```
raw/  wiki/  journal/  content/
```
Inside `raw/`, create subfolders relevant to your industry — meeting exports, emails, reports, contracts, notes.

Inside `wiki/`, create: `concepts/  projects/  people/` and two files: `index.md` and `log.md`

### Step 3 — Add CLAUDE.md
Copy the `CLAUDE.md` from this repo into your vault root. Edit the **Domain Context** section to describe your industry, your team structure, and the people you work with most.

### Step 4 — Add slash commands
Copy the `.claude/commands/` folder from this repo into your vault root. These are the commands Claude runs when you type `/briefing`, `/ingest`, etc. in Claude Code.

### Step 5 — Update priorities.md
Copy `priorities.md` from this repo and fill it in with your real projects, ongoing responsibilities, and key contacts. Claude reads this at the start of every briefing — it's your steering wheel.

### Step 6 — Drop your data into raw/
Pull your notes, email threads, meeting exports, or reports into the relevant `raw/` subfolder. Any format works — Claude will read it.

### Step 7 — Run your first ingest
Open Claude Code inside your vault directory and run:
```
/ingest
```
Claude reads your raw files and builds your first wiki pages. Open Obsidian's **Graph View** to see everything connect visually.

### Step 8 — Connect MCP tools (optional but powerful)
Connect Claude to Google Calendar, Notion, or Slack via MCP (Model Context Protocol). This lets Claude pull your real meetings and messages into the system automatically — no manual exports.

### Step 9 — Set up GitHub backup
1. Create a private GitHub repo
2. Install the Obsidian Git plugin
3. Configure it to auto-commit every 10 minutes
4. Your knowledge base is now backed up and accessible from any machine

---

## 💡 Real Use Cases by Industry

### 🏗️ Construction
- Drop site visit notes and subcontractor emails into `raw/`
- Claude builds a project page per job site — tracking decisions, open issues, and responsible parties
- Run `/debrief` after every site walkthrough — never lose a punch list item again

### 🏢 Real Estate
- Drop lease summaries, inspection reports, and tenant communications into `raw/`
- Claude builds property pages with renewal dates, maintenance history, and open action items
- Run `/briefing` each morning to see what's due, what's at risk, and who needs a follow-up

### ⚡ Energy & Utilities
- Drop maintenance logs, compliance reports, and field notes into `raw/`
- Claude tracks equipment history, open work orders, and regulatory deadlines in the wiki
- Run `/query` to pull any equipment's full history in seconds

### 💰 Finance & Professional Services
- Drop client call notes, deal memos, and review documents into `raw/`
- Claude builds client pages tracking relationship history, open items, and key decisions
- Run `/debrief` after every client call — your CRM writes itself

### 📦 Supply Chain & Logistics
- Drop vendor emails, standup notes, and route reports into `raw/`
- Claude tracks vendor performance, contract renewal dates, and open action items
- Run `/briefing` every morning — no Slack digging, no email re-reading

---

## 🗂️ Demo Files

The `demo/` folder shows exactly what the system looks like in practice:

- `demo/raw/sample-meeting-note.md` — a raw input before Claude processes it
- `demo/wiki/project-management/metro-freight-launch.md` — what Claude builds from it
- `demo/wiki/index.md` — the master catalog structure

---

## 🙏 Credits

- **[NextWork](https://www.nextwork.org)** — methodology and inspiration for this system
- **[Anthropic](https://www.anthropic.com)** — Claude Code, the AI agent that powers the wiki
- **[Andrej Karpathy](https://twitter.com/karpathy)** — vision behind AI-powered personal knowledge systems
- **[Obsidian](https://obsidian.md)** — the best local-first knowledge workspace available

---

## 📬 Questions?

Built and maintained by [Gowravi Pillarisetti](https://www.linkedin.com/in/pillarisetti-gowravi)

If you want to build this for your team — drop a comment on the LinkedIn post or DM me directly. Happy to walk you through setup.
