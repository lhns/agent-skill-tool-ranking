# Rubric

Entries pass hard gates, then get a tier. Only entries tested hands-on get a score. Tools are compared per job, never across jobs.

This replaced the score-everything method on 2026-11-13. A review of all 204 entries showed that 90% rested on README-level evidence, that their scores were effectively "guessed Fit plus Cost", and that a blind second rating disagreed by 6 points on average (see Rater noise). Scores looked more precise than they were.

## What is reliable here, and what is not

- **Reliable:** gate failures, and the pros and cons (specific, checkable facts: telemetry switches, licenses, hosted services, age, authorship).
- **Useful:** tiers and the stack, as sensible defaults for what to try first.
- **Not reliable:** any ordering among untested entries. A tier is a triage decision, not a measurement.

## Gates (pass/fail, before anything else)

A failed gate means "listed, not ranked".

| Gate | Pass condition |
| --- | --- |
| Security | No undisclosed network calls; telemetry can be switched off; no instructions that override system prompts; no known design flaw that lets untrusted input run commands with your credentials |
| License | OSI or clearly permissive for personal use; no license = fail; non-commercial and custom licenses noted |
| Maintenance | Commit or release within 6 months, or explicitly finished (static guidelines count as finished) with no open security issues |
| Platform | Works on Windows desktop or runs entirely on the remote Docker host |

The Security gate is judged at the entry's review depth (see below). A `readme` or `search` review can fail the gate but cannot certify it: read the code and pin a version before you install anything.

## Fit comes first

Fit is 0 to 4: 0 = a task you don't do, or it duplicates AGENTS.md; 2 = useful sometimes, partial overlap; 4 = core task, nothing else in the stack does it.

- **Fit below 2 is "Not for you".** The entry keeps its facts but is not compared further. No other criterion can buy that back.
- **Fit is yours to set.** The rater's Fit is a guess from what it knows about your work; `fit_by = "user"` marks the ones you set, shown as `*`. Only a Fit you set can put an entry on the Shortlist.

## Sub-scores (0 to 4 each)

| Criterion | Weight | 0 | 2 | 4 |
| --- | --- | --- | --- | --- |
| Fit | 3 | See above | | |
| Effectiveness | 3 | Made sessions worse | Helps modestly over plain Claude | Clearly better than no tool, repeatedly |
| Cost | 2 | Heavy context: many tools, long always-on text, token-hungry loops | Moderate context overhead | Near zero always-on context |
| Reliability | 2 | Misfires or crashes | Occasional misfires | Triggers exactly when wanted, stable |
| Implementation quality | 1 | Template-generated, no tests | Reasonable | Expert-written, tested, clear scope |
| Composability | 1 | All-or-nothing, conflicts | Usable alongside others | Adopt partially, removes cleanly |

**Cost means context cost for the agent only.** Money (API bills, subscriptions, hosted services), hardware and infrastructure effort go into the cons, not into Cost. Cost sub-scores from before 2026-11-13 may still mix these; they are corrected when an entry is next touched.

Effectiveness and Reliability are **unknown** without a trial. They are stored as 1 for untested entries and shown as `?`.

## Evidence, trust and review depth

Three separate things that used to be mixed:

| Evidence | Source | What it allows |
| --- | --- | --- |
| E0 | README or author claims, self-benchmarks | Tier only |
| E1 | Stars, installs, list mentions (often unverifiable) | Tier only |
| E2 | Independent third-party test with methodology; needs `evidence_source` | Tier only; Effectiveness and Reliability up to 2 once you confirm |
| E3 | Your hands-on trial, logged in the Experience log | Score; Effectiveness and Reliability up to 3 |
| E4 | Weeks of use, compared against not using it | Score; up to 4 |

- **Trust** (`official`, `own`) says who publishes it. It is not evidence that it works, and gives no bonus. Your own tools are scored like anything else, on logged use.
- **Review depth** says how the rater looked: `readme` (README only), `search` (README plus keyword search of the code), `code` (code read). Claims like "no telemetry found" carry that depth.
- Each sub-score above 1 for Effectiveness or Reliability needs its own statement in the Experience log. "It works for my team" supports Effectiveness, not Reliability.
- Evidence older than 6 months drops one level unless re-confirmed.

## Tiers

| Tier | Meaning | Rule |
| --- | --- | --- |
| Stack pick, Alternate | The default to try for a job, and next in line | Set in `data/stack.toml` |
| Shortlist | Fine to try, and you confirmed it fits | Verdict Optional, Fit 3 or 4 set by you |
| Candidate | Fine to try | Verdict Optional, Fit 2 or more |
| Watch | Promising but not ready | Verdict Watch; automatic when the repo was under 30 days old at review |
| No | Don't use it | Verdict Skip; needs a reason |
| Not for you | Fit below 2 | Automatic |

Entries carry `verdict` (Optional, Watch or Skip, with a reason after a colon); the tier is derived. Picks and alternates need Fit 2 or more and must not be under 30 days old and untested.

## Score

Only for E3 and E4: weighted sum of the six sub-scores (max 48), shown as 0 to 100. Gaps under 10 points are within rater noise.

## Compare per job

Categories only group entries; a category like "Agent safety and harness" holds sandboxes, command guards, linters and secret stores, which don't compete. The comparison unit is the job: `ranking/by-job.md` lists, for each stack job, the pick, its alternates and every entry that names the job (`jobs = ["..."]`) or cites the pick or an alternate in `overlaps`.

## Stack statuses

- **In use:** E3 or better and in regular use, or your own AGENTS.md baseline.
- **Trying now:** you are using it. No deadline. When you have an opinion, log it in the Experience log; then In use or dropped. A pick may carry an `exit_test`: what should be true to keep it.
- **Up next:** try these first, in table order.
- **Blocked:** picked, but a gate check must pass first.
- **Planned:** picked for its job; install when you work on that kind of project.

## Consistency rules

- **Telemetry:** passes the Security gate only if it can be switched off; the switch goes in the cons or stack notes.
- **Hosted services** cost a Fit point when the query itself leaks private code or names.
- **Write access to live systems:** read-only or scoped credentials by default, noted in the stack.
- **Young repos:** under 30 days old at review is Watch at best, whatever the code looks like.
- **Design flaws:** a confirmed flaw that lets untrusted input run commands with your credentials fails the Security gate unless the documented setup removes it; then the entry is Blocked until that setup is in place.

## Re-rank protocol

1. Read this rubric and Experience log rows since the last Changelog entry.
2. Turn logged trials into evidence first: update evidence, Effectiveness, Reliability, stack status.
3. Gate-check Inbox entries and give each a tier, or move it to the Watchlist with a reason. Nothing sits in the Inbox over 30 days.
4. Re-check only entries with a trigger: 90 days since `reviewed`, new major version, new Claude model generation, maintenance gate near expiry, or a logged negative experience.
5. Update the stack: one pick per job, always-on context under about 8k tokens.
6. Add one Changelog row per changed entry: ID, change, triggering evidence.

## Rater noise

On 2026-11-13 a second agent rated 15 entries blind (no access to this repo), from the same rubric and the same description of your work.

| Criterion | Exact match | Within 1 point | Mean difference |
| --- | --- | --- | --- |
| Fit | 5 of 15 | 15 of 15 | 0.67 |
| Cost | 8 of 15 | 14 of 15 | 0.53 |
| Quality | 6 of 15 | 15 of 15 | 0.60 |
| Composability | 7 of 15 | 15 of 15 | 0.53 |

- Converted to the old 0 to 100 score, the two ratings differed by 6 points on average and up to 12.5. Most old score gaps were smaller than that.
- "Try it or not" matched for 11 of 15. All 7 stack members in the sample were also judged worth trying by the second rater. The 4 disagreements were entries marked Skip (three of them without a stated reason) and one Fit guess.
- 3 of 15 entries crossed the Fit 2 line between the two ratings. That is why Fit is yours to set.
- The first rater scored Fit, Cost and Composability about 0.4 points higher on average.

Repeat this check when the rubric or the rating model changes.

## Pitfalls

- **Star inflation:** check stars per month and contributor count. Many star counts here could not be verified at all.
- **Self-benchmarks:** "65% fewer tokens" in a README stays E0 until reproduced.
- **Popularity over fit:** a hugely starred React skill is Not for you on a Scala workflow.
- **Official is not tested:** vendor or marketplace origin lowers supply-chain risk; it says nothing about whether the tool helps you.
- **Your own tools:** easy to over-rate. They need logged use like everything else.
- **Intake without use:** rating new links feels like progress but adds no evidence. Only your logged use turns a tier into a score.
- **Model drift:** scaffolding written for weaker models often hurts stronger ones. Log the model and re-check on model upgrades.
- **Prompt injection and supply chain:** skills are executable instructions. Read fully, pin a commit, diff on update.
- **Triggering:** test 3 prompts that should fire and 3 that shouldn't.
- **Token overhead:** an MCP server with 200 tools costs context every turn; prefer few coarse tools or tool filtering.
- **Double installs:** plugin plus `npx skills` gives duplicate triggers; record the install path.
- **Windows:** many skills assume bash and Unix paths; mark whether verified on your setup.
- **Conflicts with AGENTS.md:** two tools prescribing different test-before-commit procedures is a conflict, not harmless overlap.
