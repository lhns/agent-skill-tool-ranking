# How to use this doc

Add a candidate to the Inbox, log hands-on notes in the Experience log, then ask Claude to "re-rank the skill doc". Claude never edits scores without a changelog row.

1. **New skill or tool:** add a row to Inbox with the URL and the category you think it fits. One line is enough.
2. **Your experience:** add a dated row to the Experience log (entry ID, what you did, verdict). Your hands-on notes outrank every other evidence source.
3. **Re-rank:** ask Claude in any chat: "Re-rank the skill doc at \<link>". Claude reads the Rubric, scores Inbox entries, re-checks entries whose evidence is stale, updates the Ranking table and the Recommended stack, and adds a Changelog row per change.
4. **Stable IDs:** every entry has a short ID (for example `re-ghidra-bethington`). Refer to entries by ID in comments and the log so renames don't break history.
5. **Comments:** comment on any row to dispute a score or ask for a re-check; send the comment to Claude to have it act.

*Addition in this repo:* the same workflow applies to these Markdown files; for example, ask Claude to "Re-rank the skill ranking repo" (this repository). Inbox rows go in `INBOX-AND-WATCHLIST.md`, hands-on notes in `EXPERIENCE-LOG.md`, and the Ranking tables are in `ranking/`.
