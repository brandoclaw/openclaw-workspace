# TOOLS.md - Local Notes

Skills define _how_ tools work. This file is for _your_ specifics — the stuff that's unique to your setup.

## What Goes Here

Things like:

- Camera names and locations
- SSH hosts and aliases
- Preferred voices for TTS
- Speaker/room names
- Device nicknames
- Anything environment-specific

## Examples

```markdown
### Cameras

- living-room → Main area, 180° wide angle
- front-door → Entrance, motion-triggered

### SSH

- home-server → 192.168.1.100, user: admin

### TTS

- Preferred voice: "Nova" (warm, slightly British)
- Default speaker: Kitchen HomePod
```

## Why Separate?

Skills are shared. Your setup is yours. Keeping them apart means you can update skills without losing your notes, and share skills without leaking your infrastructure.

---

## OpenClaw CLI

- Node path required: `/opt/homebrew/Cellar/node@22/22.22.0_1/bin` must be in PATH
- Full command prefix: `export PATH="/opt/homebrew/Cellar/node@22/22.22.0_1/bin:/opt/homebrew/bin:$PATH" && openclaw ...`

## Discord

- Server channels require `/activation always` to respond without @mention (set per channel)
- DM channel: `channel:1477875798206582837`

---

Add whatever helps you do your job. This is your cheat sheet.

## ElevenLabs

- API Key: $ELEVENLABS_API_KEY
- Use for voiceover generation from Claude-written scripts

---

## Known Limitations

- **`write` tool sandbox** — restricted to `~/.openclaw/workspace/` only. For files outside this path, use `exec` with heredocs: `cat > /path/to/file << 'EOF'`
- **`openclaw cron run` CLI** — 30s display timeout; job continues in background. CLI timeout ≠ job failure. Always verify with `openclaw cron runs --id <id>`.
- **memory_search** — Fully operational via Gemini (`gemini-embedding-001`) as of Mar 19. Previously broken (OpenAI quota exhausted).

---

## Active Integrations

Skills/tools currently in active use:

| Tool | Purpose |
|------|---------|
| Discord | Primary chat surface (Max + @TWITC bots) |
| Telegram | Secondary surface (Max bot) |
| GitHub | Workspace auto-commit (`brandoclaw/openclaw-workspace`) |



_53 skills installed total. 16 are active/surfaced per session (including xurl, weather, openai-whisper, peekaboo, apple-notes). The remaining 37 are installed but not exposed — ask to enable any._

_Inactive/orphaned: `sag` (ElevenLabs TTS CLI) — installed globally, not surfaced, not configured. Jacob-era relic. ElevenLabs API key is live if you want to surface it._
