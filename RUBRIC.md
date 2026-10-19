# Rubric

Entries pass hard gates, get scored 0 to 4 on six weighted criteria, and are ranked only within their category. A skill and an MCP server are never ranked against each other; they meet only in the Recommended stack.

## Gates (pass/fail, before scoring)

A failed gate means "listed, not ranked".

| Gate | Pass condition |
| --- | --- |
| Security | Full SKILL.md or server code read before install; no undisclosed network calls or telemetry you can't disable; no instructions that override system prompts; install pinned to a commit or checksummed release |
| License | OSI or clearly permissive for personal use; no license = fail; non-commercial noted |
| Maintenance | Commit or release within 6 months, or explicitly finished with no open security issues |
| Platform | Works on Windows desktop or runs entirely on the remote Docker host |

## Scored criteria (0 to 4 each)

| Criterion | Weight | 0 | 2 | 4 |
| --- | --- | --- | --- | --- |
| Fit | 3 | Task you don't do, or duplicates AGENTS.md | Useful sometimes, partial overlap | Core task, nothing else in the stack does it |
| Effectiveness | 3 | Made sessions worse | Helps modestly over plain Claude | Clearly better than no tool, repeatedly |
| Cost | 2 | Heavy tokens, many tools, slow | Moderate overhead | Near zero always-on cost |
| Reliability | 2 | Misfires or crashes | Occasional misfires | Triggers exactly when wanted, stable |
| Implementation quality | 1 | Template-generated, no tests | Reasonable | Expert-written, tested, clear scope |
| Composability | 1 | All-or-nothing, conflicts | Usable alongside others | Adopt partially, removes cleanly |

Score = weighted sum (max 48), shown as 0 to 100. Sub-scores are always recorded so one criterion can change without re-deriving the rest.

## Evidence levels

Effectiveness and Reliability are both capped by the evidence level; nobody can judge stability from a README. An entry at E0 or E1 can enter the stack only with status **Trial**, never **Adopted**.

| Level | Source | Effectiveness cap |
| --- | --- | --- |
| E0 | README or author claims, self-benchmarks | 1 |
| E1 | Stars, installs, list mentions | 1 |
| E2 | Independent third-party test with methodology, or reviewed official marketplace | 2 |
| E3 | Your hands-on trial, logged | 3 |
| E4 | Weeks of use, compared against not using it | 4 |

Evidence older than 6 months drops one level unless re-confirmed.

## Trials and statuses

- **Adopted:** E3 or better and in daily use.
- **Trial:** in the stack on probation. At most 3 trials run at once, each time-boxed to 2 weeks with a written exit test (for example "adopt if it cuts exploration tool calls on a Scala repo"). Result goes in the Experience log; then Adopted or dropped.
- **Queued:** a stack pick waiting for a trial slot.
- **Alternate:** next in line if the pick fails.
- **Gate pending:** scored, but blocked until a gate check is done.
- **Baseline:** your own AGENTS.md; the reference others must beat, not ranked against them.

## Consistency rules

- **Telemetry:** passes the Security gate only if it can be switched off; the switch goes in the install notes and is applied.
- **Hosted services** (Context7, cloud embeddings) cost a Fit point when the query itself leaks private code or names.
- **Write access to live systems** (cluster, printer, KiCad files): read-only or scoped credentials by default, noted in the stack.

## Re-rank protocol

1. Read this rubric and Experience log rows since the last Changelog entry.
2. Gate-check and provisionally score Inbox entries; move each to the table or to the Watchlist with a reason. Nothing sits in the Inbox over 30 days.
3. Re-score only entries with new evidence or a trigger: 90 days since last score, new major version, new Claude model generation, maintenance gate near expiry, or a logged negative experience.
4. Score the first re-check blind (without the old row), then compare. Never re-score the whole table for consistency.
5. Update the Recommended stack: one pick per job, keeping the always-on budget under about 8k tokens; extra MCP servers go per project.
6. Add one Changelog row per changed entry: ID, change, triggering evidence.

## Ranking pitfalls

- **Star inflation:** check stars per month and contributor count. Thousands of stars with a handful of commits is a discount signal; REA's page shows about 320k stars, which is implausible.
- **Self-benchmarks:** "65% fewer tokens" in a README stays E0 until reproduced.
- **Popularity over fit:** a hugely starred React skill scores 0 on Fit for a Scala workflow.
- **Anchoring:** first scores are provisional; the first re-check is blind.
- **Model drift:** heavy scaffolding written for weaker models often hurts stronger ones. Log the model used and re-check on model upgrades.
- **Prompt injection and supply chain:** skills are executable instructions. Read fully, pin a commit, diff on update; marketplace auto-update without review fails the Security gate.
- **Triggering:** test 3 prompts that should fire and 3 that shouldn't.
- **Token overhead:** an MCP server with 200 tools costs context every turn; prefer few coarse tools or tool filtering.
- **Double installs:** plugin plus `npx skills` gives duplicate triggers; record the install path.
- **Windows:** many skills assume bash and Unix paths; mark whether verified on your setup.
- **Conflicts with AGENTS.md:** two tools prescribing different test-before-commit procedures is a conflict, not harmless overlap. AGENTS.md is itself an entry in the workflow category.
