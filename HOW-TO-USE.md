# How to use this repo

Add candidates to the Inbox, log hands-on notes in the Experience log, then ask an agent to re-rank. Every score change comes with a Changelog row.

1. **New skill or tool:** add a row to the Inbox in [INBOX-AND-WATCHLIST.md](INBOX-AND-WATCHLIST.md) with the URL and the category you think it fits. One line is enough.
2. **Your experience:** add a dated row to [EXPERIENCE-LOG.md](EXPERIENCE-LOG.md) (entry ID, model, what you did, verdict). Your hands-on notes outrank every other evidence source.
3. **Re-rank:** open this repo in Claude Code (or Codex) and say "re-rank". The agent follows [AGENTS.md](AGENTS.md): it scores Inbox entries, re-checks stale ones, edits `data/entries.toml`, regenerates the tables, updates the Recommended stack and opens a PR.
4. **Stable IDs:** every entry has a short ID (for example `re-ghidra-bethington`). Use IDs in the log and in issues so renames don't break history.
5. **Editing by hand:** change `data/entries.toml`, then run `python scripts/build.py` (Python 3.11+, no dependencies). The tables in `ranking/` and `PROS-AND-CONS.md` are generated; CI rejects hand edits to them.
