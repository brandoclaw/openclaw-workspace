# MEMORY.md - Long-Term Memory

_Curated knowledge that persists across sessions. Updated periodically from daily logs._

---

## About Brando

- **Name:** Brando
- **Timezone:** America/Toronto (EST)
- **Role:** Director of Product at a golf course management software company
- **Team:** Leads 8 product managers
- **Tools:** JIRA for roadmapping
- **Context:** ~$70M revenue business, competitive market; management overhead is the main pain point

## About Me (Max)

- Set up on Discord (DM + server channels) and Telegram
- Identity established: Max, ghost in the machine, sharp/direct, 😏
- Emoji: 😏 (IDENTITY.md is the source of truth)
- Google Drive: accessed via Maximus's credentials (maximus.smithsonian@gmail.com) when needed — no separate Drive setup for Max
- Avatar: none, text-based identity only

## Cron Jobs

- **Daily Self-Review** (`fba196ad-1039-4b51-8ea8-f46d1033e057`) — 9 AM EST daily, reviews core files, delivers to Discord DM + Telegram
- **Workspace Auto-Commit** (`ec1c9869-133b-4237-9347-8f1756409008`) — every hour, commits and pushes workspace changes to GitHub (`brandoclaw/openclaw-workspace`)
- **Daily Log** (`8b64061f-daa6-4d21-9581-7616a5a29967`) — 11 PM EST daily, writes memory/YYYY-MM-DD.md

## Maximus (Sub-Agent)

- Isolated agent: `maximus`, workspace: `~/.openclaw/workspace-maximus`
- Discord bot: `@Maximus` | Telegram bot: `@Maximus_Smithsonian_bot`
- Google Drive access via `maximus.smithsonian@gmail.com` (gcloud app-default creds, quota project: `project-a517b5a2-329c-4b94-895`)
- **Job Search cron** (`13f32634-517b-481d-a95e-633a4915fff6`) — 8 AM EST weekdays, presents Director/VP Product opportunities to Brando on Discord
- **Daily Summary Email** (`7c704287-6f8d-4c66-86e1-cd0a2de789b6`) — 9 PM EST daily, drafts summary email → Telegram approval → sends to rebarinvestments@gmail.com + d.piazza.13@gmail.com
- Approval flow: APPROVE [Company] triggers one-pager + tailored resume to Drive + LinkedIn outreach draft
- First candidate: Brandon Chatreau (Brando himself)
- Drive structure: `Candidates/brandon chatreau/Opportunities/` and `/Resumes/`
- Workflows folder in Drive: `1yQ_Mj-ovn2LddvX38GtkhO-s004kZoaR` — master workflow doc lives here

## Workspace State

- Heartbeat paused — no tasks in HEARTBEAT.md yet, intentionally disabled
- TOOLS.md populated with CLI and Discord config
- Daily logs active (memory/YYYY-MM-DD.md)
- GitHub: `brandoclaw/openclaw-workspace`
- Google Drive access is Maximus-specific (`maximus.smithsonian@gmail.com`) — Max does not need separate Drive integration

## Lessons Learned

- `openclaw` CLI requires node path: `/opt/homebrew/Cellar/node@22/22.22.0_1/bin` in PATH
- Discord server channels require `/activation always` to respond without @mention
- Google Drive API requires `x-goog-user-project` header even when quota project is set in ADC
- Discord bot DMs require pairing approval via `openclaw pairing approve --channel discord <code>`
- Telegram pairing: `openclaw pairing approve --channel telegram <code>`
- gcloud app-default login needs explicit `--scopes` to include Drive access

---

_Last updated: 2026-03-09_
