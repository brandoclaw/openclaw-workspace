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
| 8 AM weekdays | Maximus Job Search | `13f32634-517b-481d-a95e-633a4915fff6` | maximus | Haiku |
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
- First candidate: Brandon Chatreau (Brando himself)
- Drive structure: `Candidates/brandon chatreau/Opportunities/` and `/Resumes/`
- Workflows folder in Drive: `1yQ_Mj-ovn2LddvX38GtkhO-s004kZoaR` — master workflow doc lives here


## Growth (Sub-Agent — 🌱 New)

- Isolated agent: `growth`, workspace: `~/.openclaw/workspace-growth`
- **Mission:** Grow Ottawa Weekly subscriber base — target: a few hundred/week
- **Budget:** $200/month across Meta Ads + Google Ads
- **Organic:** Reddit auto-posts (r/ottawa, r/OttawaHousing, r/Gatineau, r/OttawaFood, r/ottawaevents) — no approval gate; Facebook community posts — draft-and-paste (Brando manual)
- **Paid ads approval:** 2 gates — (1) creative approval, (2) spend approval — both required before any campaign launch
- **Analytics:** Beehiiv API for subscriber tracking
- **Weekly report:** Mondays to Brando on Discord
- **Scripts:** `reddit_post.py`, `beehiiv_analytics.py`, `facebook_draft.py`
- **Credentials:** All pending — drop into `~/.openclaw/workspace-growth/.env` (see `.env.example`)

## Ottawa Weekly (Sub-Agent — Live ✅)

- Isolated agent: `ottawa-weekly`, workspace: `~/.openclaw/workspace-ottawa-weekly`
- Discord bot: `@TWITC` — delivers to Brando via TWITC Discord channel ✅
- Cron: `7c856e93` — **Thursdays 10 AM EST**
- First live run: Thursday March 13, 2026 ✅
- Pipeline: auto-saves HTML to Drive (`local news letter agent/drafts/`), notifies Brando on Discord — no approval gate
- Correct Discord channel: `1480978327945609237`
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

_Last updated: 2026-03-27_

## Recent Activity (Mar 27)
- Ottawa Weekly delivery pipeline: confirmed fixed ✅
- Wealthsimple (Mar 22): Maximus one-pager + resume pipeline ✅ complete
- Trend Pulse archived — agent config removed, cron was already paused since Mar 14
