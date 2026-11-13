# How to use this repo

Use tools from the stack, log what happened, and let an agent update the rest. Your logged use is what makes this ranking real; everything untested is only a judged shortlist.

1. **Try the stack.** The [Recommended stack](README.md#recommended-stack) lists one pick per job; start with "Up next". Some picks say what should be true to keep them. There are no deadlines.
2. **Log the result:** add a dated row to [EXPERIENCE-LOG.md](EXPERIENCE-LOG.md) (entry ID, model, what you did, how it went). Your hands-on notes outrank every other evidence source.
3. **New skill or tool:** add a row to the Inbox in [INBOX-AND-WATCHLIST.md](INBOX-AND-WATCHLIST.md), or give the agent the URL.
4. **Fit is yours:** the Fit numbers are the agent's guess unless marked `*`. Tell the agent when one is wrong; that moves entries on or off the "Not for you" list.
5. **Re-rank:** open this repo in Claude Code (or Codex) and say "re-rank". The agent follows [AGENTS.md](AGENTS.md).
6. **Compare per job:** [ranking/by-job.md](ranking/by-job.md) lists the candidates for each job. Categories only group entries.
7. **Stable IDs:** every entry has a short ID (for example `re-ghidra-bethington`). Use IDs in the log.
8. **Editing by hand:** change `data/entries.toml`, then run `python scripts/build.py` (Python 3.11+, no dependencies). The tables are generated; CI rejects hand edits to them.
