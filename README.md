# 🧠 Ops Knowledge System
### An AI-powered personal knowledge base for operational teams — built with Obsidian + Claude Code

> Based on Andrej Karpathy's methodology for AI-powered personal knowledge systems.

This is not a tech tool for tech teams. It was built for the teams that keep industries running — the ones managing sites, shifts, vendors, clients, and compliance every single day with no proper system to hold it all together.

If your team runs on WhatsApp threads, handwritten notes, and meetings nobody documents — this was made for you.

---

## 📌 What This System Does

- **Ingests** your raw notes, meeting exports, emails, and reports
- **Builds** a structured, interlinked wiki automatically — you don't write it, Claude does
- **Runs a daily briefing** every morning so you know exactly what needs attention
- **Debriefs** your meetings and surfaces every open action item
- **Answers questions** from your own data — not the internet, your notes
- **Backs up** everything to GitHub automatically every 10 minutes

---

## 🛠️ What You Need

| Tool | Cost | Purpose |
|---|---|---|
| [Obsidian](https://obsidian.md) | Free | Visual workspace — reads and displays your markdown files |
| [Claude Code](https://claude.ai/code) | Anthropic subscription | The AI agent that manages and organizes your wiki |
| [Obsidian Git Plugin](https://github.com/denolehov/obsidian-git) | Free | Auto-syncs your vault to GitHub every 10 minutes |
| [Obsidian Web Clipper](https://obsidian.md/clipper) | Free | Capture articles and web pages directly into raw/ |

---

## 🗂️ How the System Is Structured

The vault has a strict separation between **your data** and **Claude's work.**

```
ops-knowledge-system/
│
├── raw/                        ← YOUR ZONE — Claude reads this, never edits it
│   ├── meeting-exports/        # Notes from standups, site visits, client calls
│   ├── emails/                 # Key email threads worth documenting
│   ├── reports/                # Industry reports, vendor submissions, audits
│   ├── contracts/              # Contract summaries and renewal dates
│   └── notes/                  # Freeform quick captures
│
├── wiki/                       ← CLAUDE'S ZONE — all pages built and maintained here
│   ├── index.md                # Master catalog — every wiki page listed here
│   ├── log.md                  # Append-only audit trail of every change Claude makes
│   ├── concepts/               # Domain knowledge, frameworks, industry context
│   ├── projects/               # Project pages — goals, status, key decisions
│   └── people/                 # Contacts, vendors, clients, team members
│
├── journal/                    ← YOURS — daily notes, Claude only reads these
├── content/                    ← YOURS — reports, proposals, published documents
├── priorities.md               ← YOUR STEERING WHEEL — update this weekly
└── CLAUDE.md                   ← CLAUDE'S IDENTITY — tells Claude who you are
```

### The One Rule That Makes Everything Work
**`raw/` is read-only.** Drop your messy, unedited source material here.
**`wiki/` belongs to Claude.** Never edit wiki pages manually — Claude maintains them.

---

# 🚀 Part 1 — Building the Foundation

## Step 1 — Install Your Toolset

1. Download and install [Obsidian](https://obsidian.md)
2. Create a new **local vault** on your computer — this is the folder where everything lives
3. Install [Claude Code](https://claude.ai/code) — this is the AI agent you'll run from the terminal or desktop UI
4. Add the [Obsidian Web Clipper](https://obsidian.md/clipper) to your browser — lets you save articles directly into your vault

> **How they connect:** Obsidian and Claude Code both read and write to the same markdown files inside your vault folder. Obsidian shows you the visual workspace. Claude Code does the organizing.

---

## Step 2 — Create the Vault Structure

Inside your vault, create these folders manually:

```
raw/
wiki/
journal/
content/
```

Inside `raw/`, create subfolders for your data sources:
```
raw/meeting-exports/
raw/emails/
raw/reports/
raw/contracts/
raw/notes/
```

Inside `wiki/`, create subfolders and two required files:
```
wiki/concepts/
wiki/projects/
wiki/people/
wiki/index.md        ← create this as an empty file
wiki/log.md          ← create this as an empty file
```

---

## Step 3 — Configure Claude's Identity (CLAUDE.md)

Create a file called `CLAUDE.md` at the root of your vault. This is the most important file in the system — it tells Claude who you are, what industry you work in, and how to behave.

Copy the `CLAUDE.md` from this repo as your starting point, then edit the **Domain Context** section to reflect:
- Your industry and role
- The topics you work with daily
- The people and companies you interact with most
- How you want Claude to write and organize pages

> Think of CLAUDE.md as your employee onboarding document — but for an AI agent. The more specific you are, the more relevant Claude's output becomes.

---

## Step 4 — Add the Slash Commands

Create a hidden folder at your vault root:
```
.claude/commands/
```

Copy all the command files from this repo's `.claude/commands/` folder into yours. These are the commands that give you control of the entire system:

| Command | What It Does |
|---|---|
| `/ingest` | Reads raw/ files → builds structured wiki pages |
| `/query` | Ask a question → get an answer cited from your own wiki |
| `/lint` | Health check → flags broken links, missing metadata, incomplete pages |
| `/log` | Quick capture → appends a timestamped note to wiki/log.md |
| `/briefing` | Morning plan → scans calendar, logs, wiki → one focused daily plan |
| `/debrief` | Evening update → you tell Claude what happened, it updates the wiki |

---

## Step 5 — Export and Convert Your Existing Data

Populate your `raw/` folder with data you already have:

**From Claude.ai:**
- Go to Settings → Export Data → download your conversation history as JSON
- Move the JSON files into `raw/`
- Run Claude Code and ask it to convert the JSON files to markdown with YAML frontmatter
- Each converted file should include: `source`, `date`, and `topic` in the frontmatter

**From other sources:**
- Notion → export pages as markdown → drop into `raw/`
- Meeting notes → copy into `raw/meeting-exports/` as `.md` files
- Emails → paste key threads into `raw/emails/` as `.md` files
- Any text format works — Claude will read it

> **Why convert JSON to markdown?** Obsidian cannot read JSON files. Claude Code does the conversion so everything becomes readable and linkable inside your workspace.

---

## Step 6 — Run Your First Ingest

Open Claude Code inside your vault directory and run:

```
/ingest
```

Claude will:
1. Read every file in your `raw/` folder
2. Extract key concepts, projects, and people
3. Build structured wiki pages in `wiki/`
4. Update `wiki/index.md` with every new page
5. Log every change to `wiki/log.md`

**Then open Obsidian's Graph View** (left sidebar → Graph View icon). You'll see every concept, project, and person visually connected. This is your knowledge graph.

---

## Step 7 — Test Your Operational Commands

After your first ingest, test each command:

```
/query what are the main projects I'm working on?
```
→ Claude answers from your wiki with citations — not from the internet

```
/lint
```
→ Claude scans for broken links, missing frontmatter, incomplete pages

```
/log had a productive call with the vendor today — renewal on track
```
→ Claude appends a timestamped note to wiki/log.md

---

## Step 8 — Move to the Claude Code Desktop UI

Beyond the terminal, the **Claude Code Desktop UI** gives you a more visual experience for managing sessions and reviewing what Claude is doing across your vault. Install it and open your vault directory as your working project.

---

## Step 9 — Set Up GitHub Backup

1. Create a **private** GitHub repository (your real data should never be public)
2. Initialize git inside your vault folder:
```bash
git init
git remote add origin https://github.com/yourusername/your-vault.git
```
3. Install the **Obsidian Git plugin** from Obsidian's community plugins
4. Configure it to auto-commit and push every **10 minutes**

Now your knowledge base is backed up continuously and accessible from any machine. When you open your laptop after a cloud routine runs overnight, the Git plugin pulls the latest changes automatically.

---

## Step 10 — Create Your Steering Wheel (priorities.md)

Create `priorities.md` at your vault root. Copy the template from this repo and fill it in with:

- **Projects** — what you're actively building or delivering, with target dates
- **Areas** — ongoing responsibilities that never fully close
- **Resources** — topics and tools you reference regularly
- **Key People** — the people most relevant to your current work
- **Archive** — completed or paused items

Claude reads `priorities.md` at the start of every `/briefing` and `/debrief`. This is what keeps the system focused on *your* current priorities instead of surfacing old or irrelevant content.

> Update this file every Monday morning. It takes 5 minutes and makes every briefing sharper.

---

## Step 11 — Connect MCP Tools (Model Context Protocol)

MCP gives Claude direct access to your real-time data — no manual exports needed.

**Recommended connections:**
- **Google Calendar** — Claude reads your actual meetings for briefings
- **Notion** — Claude pulls pages and databases directly into raw/
- **Slack** — Claude reads threads and drops them into raw/ for ingestion

**How to connect:**
1. Open Claude Code settings
2. Navigate to MCP Connectors
3. Add each integration and authenticate

Once connected, run `/pull-sources` — Claude reaches through your MCP connectors, grabs your latest calendar events, Slack threads, and Notion pages, and drops them into `raw/` ready for the next ingest.

---

## Step 12 — Run the Daily Loop

This is the workflow that makes the system self-maintaining:

### Every Morning
```
/briefing
```
Claude reads your priorities, scans your calendar (via MCP), checks recent logs, and gives you one synthesized plan for the day. No Slack. No Gmail. No tab switching.

### Every Evening
```
/debrief
```
Claude asks what you accomplished. You tell it. Claude then:
- Updates relevant wiki pages with new information
- Creates new concept or project pages if something new surfaced
- Flags open action items
- Adjusts your priorities for tomorrow

---

## Step 13 — Set Up Cloud Routines (Automated Scheduling)

The most advanced feature: schedule your `/briefing` to run automatically in the cloud — even when your laptop is closed.

**In Claude Code:**
1. Go to Scheduled Tasks or Cloud Routines
2. Create a new routine: `/briefing` at 8:00 AM daily
3. Save and activate

**What happens:**
- At 8:00 AM, Claude runs your briefing in the cloud
- Results are written to `wiki/log.md` and pushed to GitHub
- When you open your laptop, the Obsidian Git plugin pulls the latest changes
- Your daily plan is already waiting for you — before you open a single app

---

# 📸 Screenshots

### Graph View — Everything Connected
*Every project, client, vendor, and decision — visually linked*

![Graph View](assets/graph-view.png)

### Sidebar — Clean Structure
*Raw source material on one side. Claude's wiki on the other.*

![Sidebar](assets/sidebar.png)

---

# 🗂️ Demo Files

See the `demo/` folder for examples of what the system produces:

| File | What It Shows |
|---|---|
| `demo/raw/sample-meeting-note.md` | What a raw input looks like before Claude processes it |
| `demo/wiki/project-management/metro-freight-launch.md` | What Claude builds from a raw meeting note |
| `demo/wiki/index.md` | The master catalog structure |

---

# 🙏 Credits

- **[Andrej Karpathy](https://twitter.com/karpathy)** — the original methodology for AI-powered personal knowledge systems
- **[NextWork](https://www.nextwork.org)** — course and structured learning path for building this system
- **[Anthropic](https://www.anthropic.com)** — Claude Code, the AI agent that powers the wiki
- **[Obsidian](https://obsidian.md)** — the best local-first knowledge workspace available

---

# 📬 Built By

**Gowravi Pillarisetti** — AI Ops Strategist
[LinkedIn](https://www.linkedin.com/in/pillarisetti-gowravi) · [GitHub](https://github.com/Pillarisetti-Gowravi)

Want to build this for your team? Drop a comment on the LinkedIn post or DM me directly.
