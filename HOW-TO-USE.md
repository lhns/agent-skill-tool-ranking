# How to use this repo

Try the tools in "Trying now", log what happened, and let an agent update the rest. Trials are what make this ranking real; everything untested is only a judged shortlist.

1. **Run the open trials.** The [Recommended stack](README.md#recommended-stack) shows up to three picks marked "Trying now", each with an exit test and an end date.
2. **Log the result:** add a dated row to [EXPERIENCE-LOG.md](EXPERIENCE-LOG.md) (entry ID, model, what you did, result against the exit test). Your hands-on notes outrank every other evidence source.
3. **New skill or tool:** add a row to the Inbox in [INBOX-AND-WATCHLIST.md](INBOX-AND-WATCHLIST.md), or give the agent the URL. Until a trial is logged, new candidates only get a gate check, facts and a tier.
4. **Fit is yours:** the Fit numbers are the agent's guess unless marked `*`. Tell the agent when one is wrong; that moves entries on or off the "Not for you" list.
5. **Re-rank:** open this repo in Claude Code (or Codex) and say "re-rank". The agent follows [AGENTS.md](AGENTS.md).
6. **Compare per job:** [ranking/by-job.md](ranking/by-job.md) lists the candidates for each job. Categories only group entries.
7. **Stable IDs:** every entry has a short ID (for example `re-ghidra-bethington`). Use IDs in the log.
8. **Editing by hand:** change `data/entries.toml`, then run `python scripts/build.py` (Python 3.11+, no dependencies). The tables are generated; CI rejects hand edits to them.
