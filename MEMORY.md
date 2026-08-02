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
- Avatar: none, text-based identity only

## Cron Jobs

| Time | Job | ID | Agent | Model |
|------|-----|----|-------|-------|
| 9 AM daily | Daily Self-Review | `fba196ad-1039-4b51-8ea8-f46d1033e057` | main | default |
| Daily at midnight EST | Workspace Auto-Commit | `ec1c9869-133b-4237-9347-8f1756409008` | main | Haiku |
| 11 PM daily | Daily Log | `8b64061f-daa6-4d21-9581-7616a5a29967` | main | Haiku |
**Retired crons (do not recreate):**
- `13f32634` — Maximus Job Search (retired Apr 7)
- `7c704287` — Weekly Summary Email (retired Apr 7)
- `7c856e93` — Ottawa Weekly Newsletter (retired May 19)

**⚠️ Known false positives from self-review cron (ignore permanently):**
- `5448df10`, `a62cea1a`, `d90dfaa9` — **not in the scheduler**. Confirmed Apr 11 + Apr 13. `removed: false` on all three. Only 4 live jobs exist. Self-review re-flags these from stale output — do not action.
- **AGENTS.md Maximus P1** — self-review kept flagging Maximus job search section as "reads like live workflow." **Resolved Apr 11** — section now shows 🪦 RETIRED, re-enable instructions removed. If self-review flags this again, it is stale.


## Maximus (Sub-Agent — 🪦 RETIRED as of Apr 7, 2026)

- Fully removed. Do not recreate.



## Ottawa Weekly (Sub-Agent — 🪦 RETIRED as of May 19, 2026)

- Cron `7c856e93` deleted. Agent workspace removed. Do not recreate.

## Workspace State

- Heartbeat active but HEARTBEAT.md is intentionally empty — no periodic tasks configured yet
- TOOLS.md populated with CLI and Discord config
- Daily logs active (memory/YYYY-MM-DD.md)
- GitHub: `brandoclaw/openclaw-workspace`

## Known Limitations

- **memory_search** — powered by Gemini (`gemini-embedding-001`). Fully operational as of Mar 19.
- **`write` tool sandbox** — sandboxed to `~/.openclaw/workspace` only. For other agent workspaces, use `exec` with heredocs (`cat > file << 'EOF'`).
- **`openclaw cron run` CLI** — has a 30s display timeout; jobs continue running in background. A timeout message from the CLI is NOT a failure indicator — check `openclaw cron runs --id <id>` to verify actual status.
- **Delivery false-error pattern** — `⚠️ ✉️ Message failed` + `delivered: true` = delivery actually succeeded. This is a gateway quirk, not a real failure.
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

_Last updated: 2026-08-01_

## API Outage — July 25–31, 2026

- Anthropic API usage limits hit July 25, lasted through July 31. All Claude-based crons (self-review, daily log, auto-commit) failed for 6 consecutive days.
- Access restored midnight UTC Aug 1 (= July 31 8 PM EST). All crons resumed normally.
- **6-day memory gap:** No daily logs exist for July 25–30. Not a cleanup error — crons simply failed to write them.
- **Git gap:** Auto-commit missed July 25–31. No workspace changes occurred during that window, so no data was lost — just no commits.
- AGENTS.md had stale "every-3-hour" text for auto-commit — fixed Aug 1.

## Jacob (Sub-Agent — 🪦 RETIRED as of May 19, 2026)

- Fully removed. Do not recreate.

