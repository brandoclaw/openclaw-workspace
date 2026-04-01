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

| Time | Job | ID | Agent | Model |
|------|-----|----|-------|-------|
| ~~8 AM weekdays~~ | ~~Maximus Job Search~~ | ~~`13f32634-517b-481d-a95e-633a4915fff6`~~ | ~~maximus~~ | **PAUSED** as of Mar 31 |
| 9 AM daily | Daily Self-Review | `fba196ad-1039-4b51-8ea8-f46d1033e057` | main | Sonnet |
| Every 3 hours | Workspace Auto-Commit | `ec1c9869-133b-4237-9347-8f1756409008` | main | Haiku |
| 9 PM **Mondays only** | Weekly Summary Email Draft | `7c704287-6f8d-4c66-86e1-cd0a2de789b6` | maximus | Sonnet |
| 11 PM daily | Daily Log | `8b64061f-daa6-4d21-9581-7616a5a29967` | main | Haiku |
| 10 AM Thursdays | Ottawa Weekly Newsletter | `7c856e93-5661-42f3-bc7e-bba14ab83710` | ottawa-weekly | Sonnet |


## Maximus (Sub-Agent)

- Isolated agent: `maximus`, workspace: `~/.openclaw/workspace-maximus`
- Discord bot: `@Maximus` | Telegram bot: `@Maximus_Smithsonian_bot`
- Google Drive access via `maximus.smithsonian@gmail.com` (gcloud app-default creds, quota project: `project-a517b5a2-329c-4b94-895`)
- **Job Search cron** (`13f32634-517b-481d-a95e-633a4915fff6`) — 8 AM EST weekdays, searches ONLY the target company list (see below), presents Product Manager, Director, and VP Product roles to Brando on Discord
- **⚠️ Target companies only** — no roles posted unless from this list (Drive doc `1iyo8O56n3yzl7a6xS3QX31htuRIOeU2nPQeJabhH2VE`):
  Netflix, Wealthsimple, Google, Shopify, Microsoft, OpenAI, Anthropic, Meta, Amazon, Tesla, SpaceX, Anduril
- **Weekly Summary Email** (`7c704287-6f8d-4c66-86e1-cd0a2de789b6`) — 9 PM EST Mondays, drafts summary email → Telegram approval → sends to rebarinvestments@gmail.com + d.piazza.13@gmail.com
- Approval flow: APPROVE [Company] triggers one-pager + tailored resume to Drive + key contact research (no automated LinkedIn outreach — Maximus identifies contacts, Brando reaches out himself)
- ⚠️ **APPROVE/SKIP decisions are session-volatile** — not tracked in long-term memory. On a fresh session, check recent Maximus Discord posts to see what's pending or already actioned.
- **`APPROVE ALL`** is the primary command — runs the full pipeline for every pending role at once. `APPROVE [Company]` for single-role approvals.
- **Expiry rule:** Roles unanswered after 5 business days are auto-archived to the Pending Roles Archive doc in Drive. No action taken — just logged.
- **Pending Roles Archive Drive doc:** `1Z9j8r1xxUap9nUcMHCP9bbkVZ0EB1KnSPqT89J7TKKo` — created Mar 28, 2026
- **Approval cadence:** Brando typically batch-approves every 3–5 days via `APPROVE ALL`, not same-day per role. Maximus should frame backlog summaries accordingly.
- **Netflix scope:** Principal PM roles included (in addition to Director/VP/GPM).
- First candidate: Brandon Chatreau (Brando himself)
- Drive structure: `Candidates/brandon chatreau/Opportunities/` and `/Resumes/`
- Workflows folder in Drive: `1yQ_Mj-ovn2LddvX38GtkhO-s004kZoaR` — master workflow doc lives here



## Ottawa Weekly (Sub-Agent — Live ✅)

- Isolated agent: `ottawa-weekly`, workspace: `~/.openclaw/workspace-ottawa-weekly`
- Discord bot: `@TWITC` — delivers to Brando via TWITC Discord channel ✅
- Cron: `7c856e93` — **Thursdays 10 AM EST**
- First live run: Thursday March 13, 2026 ✅
- Pipeline: auto-saves HTML to Drive (`local news letter agent/drafts/`), notifies Brando on Discord — no approval gate
- Correct Discord channel: `1480978327945609237`
- **Draft in Drive = done.** No tracking of whether Brando pasted into Beehiiv — that's fully his call, no follow-up needed.
- **Draft lifecycle:** Drafts older than 2 weeks are considered stale and auto-archived (no action taken, no Beehiiv send). Brando's call if he wants to use them.
- Full context lives in the ottawa-weekly agent workspace — do not manage from here

## Workspace State

- Heartbeat active but HEARTBEAT.md is intentionally empty — no periodic tasks configured yet
- TOOLS.md populated with CLI and Discord config
- Daily logs active (memory/YYYY-MM-DD.md)
- GitHub: `brandoclaw/openclaw-workspace`
- Google Drive access is Maximus-specific (`maximus.smithsonian@gmail.com`) — Max does not need separate Drive integration

## Known Limitations

- **memory_search** — powered by Gemini (`gemini-embedding-001`). Fully operational as of Mar 19.
- **`write` tool sandbox** — sandboxed to `~/.openclaw/workspace` only. For other agent workspaces, use `exec` with heredocs (`cat > file << 'EOF'`).
- **`openclaw cron run` CLI** — has a 30s display timeout; jobs continue running in background. A timeout message from the CLI is NOT a failure indicator — check `openclaw cron runs --id <id>` to verify actual status.
- **@TWITC bot DMs** — `groupPolicy` restriction prevents @TWITC from DMing Brando directly. Cross-bot routing (via Max bot) is the only workaround.
- **`channels.discord.accounts.*` allowlist key** — NOT supported; crashes the gateway. Do not attempt to restrict bot DMs via allowlist config. Cross-bot routing is the only workaround for restricted DMs.

## Lessons Learned

- `openclaw` CLI requires node path: `/opt/homebrew/Cellar/node@22/22.22.0_1/bin` in PATH
- Discord server channels require `/activation always` to respond without @mention
- Google Drive API requires `x-goog-user-project` header even when quota project is set in ADC
- Discord bot DMs require pairing approval via `openclaw pairing approve --channel discord <code>`
- Telegram pairing: `openclaw pairing approve --channel telegram <code>`
- gcloud app-default login needs explicit `--scopes` to include Drive access
- `channels.discord.accounts.*` does not support an allowlist key — it crashes the gateway. Cross-bot routing is the only workaround for restricted DMs.

_Last updated: 2026-04-01_

## Jacob (Sub-Agent — 🎵 Live)

- Isolated agent: `jacob`, workspace: `~/.openclaw/workspace-jacob`
- **Trigger:** Airtable webhook → `Status` = `Ready to Generate`
- **Webhook URL:** `https://subclavate-deacon-isogeothermic.ngrok-free.dev/webhook`
- **Pipeline:** Airtable prompts → GPT-4o lyrics → Suno (Playwright) → Telegram approval → Drive upload → feedback loop (max 5 iterations)
- **Approvers:** Brando (TELEGRAM_APPROVER_1) + +14167323117
- **Services:** ngrok (`com.jacob.ngrok`) + webhook server (`com.jacob.webhook`) — both auto-start on boot via launchd
- **Credentials:** All pending — drop into `~/.openclaw/workspace-jacob/.env`

## Recent Activity (Apr 1)
- Maximus pipeline now produces: one-pager + resume + cover letter + key contacts per role ✅
- `APPROVE ALL` confirmed as primary approval command
- Role expiry reduced to 5 business days → auto-archive to Drive
- Growth agent archived (Mar 29)
- Ottawa Weekly Issue #4 (`TWITC_Draft_2026-03-20.html`) — marked stale/abandoned (11 days old, no Beehiiv send confirmed) ✅ closed
- Ottawa Weekly Issue #5 — on Drive, Brando's call to send
