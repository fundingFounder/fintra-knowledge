---
type: knowledge
category: automation
tags: [secretary, cron, briefing, automation, persona]
---

# The Secretary — Daily Task Briefing

> An automated executive assistant that governs your workday with 10 actionable tasks every morning at 9:30 AM IST.

## 🔗 Connections

- **Persona:** `~/.hermes/personas/the-council/secretary.md`
- **Skill:** `secretary-briefing` (Hermes skill)
- **Cron Job:** `0ed6a332cbfb` — 9:30 AM IST daily, all 7 days
- **Delivers to:** Telegram (Home channel)

---

## 📐 How It Works

1. **9:30 AM IST** — Cron job triggers The Secretary persona
2. **Scans** all project task files, git status, health checks, Obsidian vault, GitHub issues
3. **Generates** exactly 10 prioritized, actionable tasks
4. **Delivers** briefing to Telegram in the format:
   - 🔴 URGENT (1-2 tasks)
   - 🟡 PRIORITY (3-4 tasks)
   - 🟢 QUICK WINS (2-3 tasks)
   - 🏠 HOUSEKEEPING (1-2 tasks)
   - 📊 STATUS CHECK (all services)
   - 💡 YESTERDAY'S WINS

5. **Post-briefing** — Creates session note in Obsidian vault, pushes to Git, rebuilds web graph

## 📐 Task Sources

| Source | What It Checks |
|--------|---------------|
| Task files | `task.md`, `todo.md` in each project |
| GitHub | Open issues & PRs in `fundingFounder` repos |
| Obsidian Vault | Session notes, Decision Log, project known issues |
| Health checks | fintra-admin, fintrahq, tenantpwa, fintra-graph, Supabase edge functions |
| Git status | Uncommitted changes across all project repos |

## 📐 Task Selection Rules

- **Balanced** across all projects (not all 10 on one project)
- **Mixed difficulty**: quick wins + medium + deep work
- **Priority weighted** by what's broken (down sites = always task #1)
- **Never repeats** completed work (checks yesterday's session note)
- **Always includes** file paths and commands

---

## 📋 Related

- [[Dibyendu Mondal]]
- [[FinTra - Project Overview]]
- [[Percy — Project Overview]]