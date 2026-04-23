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
| 9 AM daily | Daily Self-Review | `fba196ad-1039-4b51-8ea8-f46d1033e057` | main | Sonnet |
| Every 3 hours | Workspace Auto-Commit | `ec1c9869-133b-4237-9347-8f1756409008` | main | Haiku |
| 11 PM daily | Daily Log | `8b64061f-daa6-4d21-9581-7616a5a29967` | main | Haiku |
| 10 AM Thursdays | Ottawa Weekly Newsletter | `7c856e93-5661-42f3-bc7e-bba14ab83710` | ottawa-weekly | Sonnet |

**Retired crons (do not recreate):**
- `13f32634` — Maximus Job Search (retired Apr 7)
- `7c704287` — Weekly Summary Email (retired Apr 7)

**⚠️ Known false positives from self-review cron (ignore permanently):**
- `5448df10`, `a62cea1a`, `d90dfaa9` — **not in the scheduler**. Confirmed Apr 11 + Apr 13. `removed: false` on all three. Only 4 live jobs exist. Self-review re-flags these from stale output — do not action.
- **AGENTS.md Maximus P1** — self-review kept flagging Maximus job search section as "reads like live workflow." **Resolved Apr 11** — section now shows 🪦 RETIRED, re-enable instructions removed. If self-review flags this again, it is stale.


## Maximus (Sub-Agent)

- Isolated agent: `maximus`, workspace: `~/.openclaw/workspace-maximus`
- Discord bot: `@Maximus` | Telegram bot: `@Maximus_Smithsonian_bot`
- Google Drive access via `maximus.smithsonian@gmail.com` (gcloud app-default creds, quota project: `project-a517b5a2-329c-4b94-895`)
- **Job Search cron** (`13f32634`) — **retired Apr 7, 2026. Fully removed. Do not recreate.**
- **Weekly Summary Email cron** (`7c704287`) — **retired Apr 7, 2026. Fully removed. Do not recreate.**



## Ottawa Weekly (Sub-Agent — Live ✅)

- Isolated agent: `ottawa-weekly`, workspace: `~/.openclaw/workspace-ottawa-weekly`
- Discord bot: `@TWITC` — delivers to Brando via TWITC Discord channel ✅
- Cron: `7c856e93` — **Thursdays 10 AM EST**
- First live run: Thursday March 13, 2026 ✅
- Pipeline: auto-saves HTML to Drive (`local news letter agent/drafts/`), notifies Brando on Discord — no approval gate
- Correct Discord channel: `1480978327945609237`
- **Draft in Drive = done.** No tracking of whether Brando pasted into Beehiiv — that's fully his call, no follow-up needed.
- **Issue #6 (Easter weekend, Apr 2 draft):** Sent by Brando on Apr 5 ✅
- **Issue #7 (Apr 9 draft):** Sent by Brando on Apr 13 ✅
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

_Last updated: 2026-04-23_

## Jacob (Sub-Agent — 🎵 Live ✅)

- Isolated agent: `jacob`, workspace: `~/.openclaw/workspace-jacob`
- **Trigger:** Airtable webhook → `Status` = `Paid` (Orders table)
- **Webhook URL:** `https://subclavate-deacon-isogeothermic.ngrok-free.dev/webhook` (static ngrok domain)
- **Pipeline:** Airtable prompts → GPT-4o lyrics → Suno (headed Chrome) → Telegram approval → Drive upload
- **Approvers:** Brando `8776720992` + Tim `8720480894` (both receive approval pings)
- **Drive folder:** `songs/` — ID `1ndjRomNL1EGqcvAE-7nJDJC6ad4SlAx2` (Maximus Drive)
- **Services:** ngrok (`com.jacob.ngrok`) + webhook server (`com.jacob.webhook`) — both auto-start on boot via launchd (port 5055)
- **Credentials:** All configured in `~/.openclaw/workspace-jacob/.env` ✅
- **Drive upload:** Confirmed working end-to-end (Apr 1) ✅
- **First order:** The Thunder (recNcU81XzXqgL9bk) — songs uploaded to Drive Apr 1
- **Suno session:** `.suno_session.json` — if expired, run `python3 scripts/suno_login.py`
- **Airtable status field:** Only `Paid` / `Pending Payment` are valid values — Telegram handles all status notifications
- **Airtable webhook automation:** Confirmed in place as of Apr 2 ✅
- **Webhook payload format:** Airtable sends `{"recordId": "GDA..."}` — this is the `Order ID` formula field value, NOT the Airtable `rec` ID
- **Lookup flow:** `webhook_server.py` calls `find_record_by_order_id()` in `airtable_client.py` to resolve GDA... → rec ID, then fetches full record to check Status
- **Bug fixed Apr 2:** Two issues — (1) `recordId` camelCase wasn't being extracted, (2) Status was read from payload instead of fetched from Airtable API. Both fixed. Pipeline confirmed working end-to-end.
- **Crash-loop note:** launchd `com.jacob.webhook` will show port 48 errors if server is already running (harmless — real process holds the port fine)

