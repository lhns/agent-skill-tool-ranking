# Changelog

| Date | ID | Change | Evidence |
| --- | --- | --- | --- |
| 2026-10-19 | mem-1ctx | Added, 44, Watch | Repo source and docs read; alpha, started 2026-10-04 |
| 2026-10-19 | mem-optmem | Listed as gate failure (License) | No LICENSE file; README states none |
| 2026-10-19 | mem-agentmemory | Moved to new category Memory and context; score unchanged | New category |
| 2026-10-19 | infra-remote-docker | Added, 88, stack pick (In use) for Docker on the remote host | Your own tool, in daily use (E3) |
| 2026-10-19 | infra-docker-ckreiling | Fit 3 to 1, 52 to 40, pick to Skip | remote-docker plus the docker CLI covers the job without an MCP |
| 2026-10-19 | x-hermes-godmode | Fit 1 to 3, 27 to 40, Skip to Optional | Fit set by user |
| 2026-10-19 | x-hermes-godmode | Verdict reason no longer assumes your need; Fit stays 1 until you set it | User: need is the user's call |
| 2026-10-19 | x-hermes-godmode | Gate failure (Security) to ranked, 27, Skip | User-intended behavior is not a security failure; scored on fit only, effectiveness not assessed |
| 2026-10-19 | wf-godmode-noobygains | Added, 27, Skip | Hook and SKILL.md read; near-clone of superpowers |
| 2026-10-19 | x-hermes-godmode | Listed as gate failure (Security) | Jailbreak skill; skills.sh audits fail |
| 2026-10-19 | stack | Stack moved to `data/stack.toml` and generated into README with links and scores; statuses renamed (In use, Trying now, Up next, Blocked, Planned); first three picks are Up next, not Trial, since no trial is logged yet | User found the status column confusing |
| 2026-10-19 | lang-rust-async | Now the pick for a new job, Rust and Go idioms; lang-go-samber and lang-rust-apollo are its alternates | Had stack-style verdicts without a stack row |
| 2026-10-19 | all | Non-stack verdicts normalized to Optional, Watch or Skip with an optional reason | Mixed formats |
| 2026-10-19 | build-harness2 | Added, 25, Watch | Repo page, arXiv 2610.14224 abstract, Wavect write-up (not hands-on); 10.3k stars on 3 commits |
| 2026-10-19 | repo | Ranking tables now generated from `data/entries.toml` by `scripts/build.py`; AGENTS.md re-rank workflow; CI check | Two hand-arithmetic slips in the doc era |
| 2026-10-19 | lang-scala-direct-style | Added, 54, Queued for Ox projects only | Repo, SKILL.md and chapters read; 69 stars (E1) |
| 2026-10-19 | safe-tacit | Added, 31, Watch | Repo and paper read; nightly compiler, no Windows path |
| 2026-10-19 | harness-atc | Added, 27, Skip | Standalone agent, not a component; one author, two months old |
| 2026-10-19 | all | Second pass: about 90 entries added from 10 discovery sources; 9 new categories | Source pages, repo pages, skills.sh audit badges (E0 to E2) |
| 2026-10-19 | stack | New picks: SkillSpector, official LSP plugins, Skill\_Seekers, mcp-nixos, duckdb-skills, kicad-happy, vibing-steampunk, HA official MCP, zigbee2mqtt-mcp, and others | Highest score per job |
| 2026-10-19 | sec-official | Replaces trailofbits as security pick (69 vs 58) | Reviewed official marketplace = E2 |
| 2026-10-19 | fe-webapp-testing | Replaces playwright-cli as testing pick (71 vs 69, tie) | Reviewed official marketplace = E2 |
| 2026-10-19 | ee-kicad-happy | Becomes PCB review and simulation pick; spicebridge drops to alternate | Covers SPICE, EMC, BOM; 729 commits |
| 2026-10-19 | out-caveman | Moved from gate failure to ranked Skip (31) | New telemetry rule: passes if it can be switched off |
| 2026-10-19 | wf-gstack, wf-loki-mode, fe-design-mobile, x-101-superpowers, x-reddit-automation, and 6 more | Listed as gate failures | Permission-bypass hooks, BSL license, Snyk High, name squatting, archived repos |
| 2026-10-19 | all | Reliability now capped by evidence; all E0 to E1 entries re-scored down | Adversarial review: README can't show stability |
| 2026-10-19 | re-rea | Trial to Gate pending: security | Anomalous stars (about 320k, 52k in a day), undocumented transport, own Ghidra driver |
| 2026-10-19 | re-ghidra-bethington | Kept as your pick; pyghidra-mcp ties it (60 vs 58) | Bridge already provides auth |
| 2026-10-19 | wf-agentsmd | Moved to Baseline | Your own reference shouldn't be ranked against others |
| 2026-10-19 | k8s-containers | Read-only and scoped ServiceAccount required | Write access to a live cluster |
| 2026-10-19 | docs-context7 | Fit 3 to 2, limited to non-Scala | Metals covers Scala; hosted service sees queries |
| 2026-10-19 | wf-mattpocock | Reduced to grill-with-docs only | diagnosing-bugs duplicates AGENTS.md |
| 2026-10-19 | wr-humanizer | Global to per project | Always-on budget |
| 2026-10-19 | all | Initial provisional ranking of 40 entries | Repo pages, issues, third-party comparisons (E0 to E2) |
