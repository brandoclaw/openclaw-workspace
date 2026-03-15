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
| 10 AM daily | Trend Pulse Daily | `d90dfaa9-479f-4d0b-91da-41e566941c9b` | trendpulse | Sonnet |
| Every 3 hours | Workspace Auto-Commit | `ec1c9869-133b-4237-9347-8f1756409008` | main | Haiku |
| 9 PM **Mondays only** | Weekly Summary Email Draft | `7c704287-6f8d-4c66-86e1-cd0a2de789b6` | maximus | Sonnet |
| 11 PM daily | Daily Log | `8b64061f-daa6-4d21-9581-7616a5a29967` | main | Haiku |

## Maximus (Sub-Agent)

- Isolated agent: `maximus`, workspace: `~/.openclaw/workspace-maximus`
- Discord bot: `@Maximus` | Telegram bot: `@Maximus_Smithsonian_bot`
- Google Drive access via `maximus.smithsonian@gmail.com` (gcloud app-default creds, quota project: `project-a517b5a2-329c-4b94-895`)
- **Job Search cron** (`13f32634-517b-481d-a95e-633a4915fff6`) — 8 AM EST weekdays, searches ONLY the target company list (see below), presents Director/VP Product opportunities to Brando on Discord
- **⚠️ Target companies only** — no roles posted unless from this list (Drive doc `1iyo8O56n3yzl7a6xS3QX31htuRIOeU2nPQeJabhH2VE`):
  Netflix, Wealthsimple, Google, Shopify, Microsoft, OpenAI, Anthropic, Meta, Amazon, Tesla, SpaceX, Anduril
- **Weekly Summary Email** (`7c704287-6f8d-4c66-86e1-cd0a2de789b6`) — 9 PM EST Mondays, drafts summary email → Telegram approval → sends to rebarinvestments@gmail.com + d.piazza.13@gmail.com
- Approval flow: APPROVE [Company] triggers one-pager + tailored resume to Drive + key contact research (no automated LinkedIn outreach — Maximus identifies contacts, Brando reaches out himself)
- First candidate: Brandon Chatreau (Brando himself)
- Drive structure: `Candidates/brandon chatreau/Opportunities/` and `/Resumes/`
- Workflows folder in Drive: `1yQ_Mj-ovn2LddvX38GtkhO-s004kZoaR` — master workflow doc lives here

## Trend Pulse (Sub-Agent)

- Isolated agent: `trendpulse`, workspace: `~/.openclaw/workspace-trendpulse`
- Runs daily at 10 AM EST via cron (`d90dfaa9`)
- Pipeline: scoring engine v2 (YouTube Data API velocity + Google Trends + TikTok static hashtags) → ElevenLabs voiceover (Adam voice, ID: `pNInz6obpgDQGcFmaJgB`) → video assembly → YouTube upload
- YouTube OAuth: `~/.openclaw/youtube_token.pkl` (scopes: upload, delete, gmail.send)
- YouTube OAuth client: `~/.openclaw/youtube_client_installed.json`
- 3-tier hashtag strategy: broad reach + niche-specific + long-tail (20 hashtags/video)
- Topic-aware Pexels image queries (Finance → charts/money, AI → robots/code)
- ⚠️ FFmpeg on this machine lacks libfreetype — drawtext/caption overlay NOT available
- ⚠️ Google Trends hits 429 rate limits — handled with retry/backoff logic
- Videos saved to Drive before upload

## Ottawa Weekly (Sub-Agent — Live)

- Isolated agent: `ottawa-weekly`, workspace: `~/.openclaw/workspace-ottawa-weekly`
- Discord bot: `@TWITC` — DMs working, approval flow confirmed live
- Cron: `7c856e93` — **Thursdays 10 AM EST**
- First live run: Thursday March 13, 2026 ✅
- Full context lives in the ottawa-weekly agent workspace — do not manage from here

## Workspace State

- Heartbeat active but HEARTBEAT.md is intentionally empty — no periodic tasks configured yet
- TOOLS.md populated with CLI and Discord config
- Daily logs active (memory/YYYY-MM-DD.md)
- GitHub: `brandoclaw/openclaw-workspace`
- Google Drive access is Maximus-specific (`maximus.smithsonian@gmail.com`) — Max does not need separate Drive integration

## Known Limitations

- **memory_search unavailable** — OpenAI embeddings quota exhausted. Fallback: manually read MEMORY.md + recent memory/YYYY-MM-DD.md files directly.
- **`write` tool sandbox** — sandboxed to `~/.openclaw/workspace` only. For other agent workspaces, use `exec` with heredocs (`cat > file << 'EOF'`).
- **`openclaw cron run` CLI** — has a 30s display timeout; jobs continue running in background. A timeout message from the CLI is NOT a failure indicator — check `openclaw cron runs --id <id>` to verify actual status.

## Exempt from Plan-First Rule (Cron / Background Jobs)

These automated pipelines run without requiring Brando's approval:
- Workspace Auto-Commit (`ec1c9869`)
- Daily Self-Review (`fba196ad`)
- Daily Log (`8b64061f`)
- Maximus Job Search (`13f32634`)
- Weekly Summary Email Draft (`7c704287`) — draft only, send requires Telegram approval
- Ottawa Weekly Newsletter (`7c856e93`) — draft only, save to Drive requires APPROVE

## Lessons Learned

- `openclaw` CLI requires node path: `/opt/homebrew/Cellar/node@22/22.22.0_1/bin` in PATH
- Discord server channels require `/activation always` to respond without @mention
- Google Drive API requires `x-goog-user-project` header even when quota project is set in ADC
- Discord bot DMs require pairing approval via `openclaw pairing approve --channel discord <code>`
- Telegram pairing: `openclaw pairing approve --channel telegram <code>`
- gcloud app-default login needs explicit `--scopes` to include Drive access

---

## Trend Pulse YouTube Channel
- Handle: @maxsmithsonian
- Description (confirmed by Brando, Mar 10): "Your daily pulse on the trends shaping finance, AI, and the world — distilled into sharp, no-fluff breakdowns every day."

_Last updated: 2026-03-15_
