# Pros and cons

One row per entry, grouped like the Ranking. Stars are as shown on GitHub on 2026-10-19 and are E1 evidence only.

## Workflow and process

| ID | Stars | Pros | Cons | Overlaps with |
| --- | --- | --- | --- | --- |
| wf-agentsmd | n/a | Short, tuned to your habits, encodes model delegation and ADRs | Grows by hand; no enforcement beyond the model reading it | All workflow entries |
| wf-mattpocock | \~294k | Pick single skills; grill-with-docs writes a glossary and ADRs, matching your setup | grill-me sometimes starts implementing (#240) and bundles several questions per turn (#221); plugin plus `npx skills` installs everything twice | superpowers, gsd, turbo |
| wf-superpowers | \~300k | Most-discussed framework; TDD and worktree isolation built in | About 3x vanilla time in one test; plans over 3,000 lines (#512); mandatory loop competes with your delegation rules; telemetry ping | AGENTS.md, gsd, turbo |
| wf-turbo | 404 | Small; `/finalize` adds a cross-model peer review | Needs Codex installed for review; barely used anywhere | AGENTS.md |
| wf-neckbeard | 123 | Evidence ledger per change, ships an eval harness, explicitly not a persona | Built for Hermes first; heavy stage model; small user base | AGENTS.md |
| wf-gsd | 10.5k | Fresh-context subagents per phase fight context rot; `STATE.md` survives sessions | About 6x the tokens and 5x the time of vanilla in one test; heaviest of all | AGENTS.md, superpowers |

## Code intelligence

| ID | Stars | Pros | Cons | Overlaps with |
| --- | --- | --- | --- | --- |
| ci-codegraph | \~74k | Rust kernel; Scala at full support; one MCP tool; auto-syncs on save; 100% local | Author benchmarks only (E0); leaves about 80% more context resident in long sessions (its own measurement); telemetry on until `codegraph telemetry off` | graphify, code-review-graph |
| ci-graphify | \~128k | Also graphs docs, PDFs and media; no vector store; explains each edge | Docs pass costs model tokens; README pushes the paid cloud; rebuild-on-demand, not live | codegraph |
| ci-crg | \~32k | Risk-scored PR reviews, GitHub Action, blast radius | 30 MCP tools by default (filterable); Scala support less explicit | codegraph |

## Language and library docs

| ID | Stars | Pros | Cons | Overlaps with |
| --- | --- | --- | --- | --- |
| lang-metals-mcp | \~2.3k (Metals) | Real compiler diagnostics, symbols, tests and deps for Scala; official | Needs a working Metals build per project; tool output can be large | codegraph (partly) |
| docs-context7 | \~63k | Fresh library docs on demand; CLI plus skill mode keeps context small | Closed backend; community docs with no accuracy guarantee; rate limits unpublished | none |

## Reverse engineering

| ID | Stars | Pros | Cons | Overlaps with |
| --- | --- | --- | --- | --- |
| re-ghidra-bethington | \~4.5k | Headless server; Bearer token auth; refuses non-loopback binds without a token; scripts off by default; file-root sandbox; lazy tool groups | 209 tools if you load everything; pinned to Ghidra 12.1.3; Docker setup not fully documented | REA, pyghidra |
| re-pyghidra | 426 | Official Docker image, HTTP by default, 18 tools, whole-project analysis | No auth; beta; small community | bethington |
| re-android | \~8.2k | jadx-based APK/XAPK/JAR decompile; pulls out HTTP APIs and auth; recovers R8 names | PowerShell scripts experimental; needs JDK 17+ and jadx installed | REA (JADX backend) |
| re-rea | \~320k (anomalous) | One orchestrator over Ghidra, IDA, Hopper, JADX, binwalk, unblob, Rizin, GDB, TShark | Star count implausible (52k in a day); README warns copies are not official, so install only `rea-agents` from npm; transport undocumented; drives Ghidra 12.1.4 itself, not via ghidra-mcp | ghidra-mcp, Android RE |
| re-ghidra-laurie | \~11.3k | Most popular Ghidra bridge; headless via PyGhidra | No auth; few commits; 38 open PRs | bethington, pyghidra |

## Security review

| ID | Stars | Pros | Cons | Overlaps with |
| --- | --- | --- | --- | --- |
| sec-trailofbits | \~7.6k | Expert-written code-audit skills: variant analysis, Semgrep rules, differential review, supply-chain risk | Narrow; little for ops or cloud security | mukul975 |
| sec-mukul | \~33.7k | Very broad SOC and threat-hunting coverage, ATT&CK mapping | Not affiliated with Anthropic; about 817 template-like skills; contradictory counts; promotes its own platform | trailofbits |

## Kubernetes and infrastructure

| ID | Stars | Pros | Cons | Overlaps with |
| --- | --- | --- | --- | --- |
| k8s-containers | \~2.2k | Single Go binary; talks to the API directly; `read_only` mode | Helm support limited to install, list, uninstall | Flux159 |
| k8s-flux159 | \~1.6k | kubectl and Helm, diagnose prompt | "Non-destructive" mode still allows apply, patch, scale | containers |
| infra-neckbeard-bealesh | 6 | Deterministic Go CLI plus versioned module catalog; cost estimates | Pre-alpha; targets AWS, GCP, Azure, not self-hosted | none |

## Web frontend and testing

| ID | Stars | Pros | Cons | Overlaps with |
| --- | --- | --- | --- | --- |
| fe-playwright-cli | \~13k | Microsoft's recommended agent path; fewer tokens than Playwright MCP | Vendor recommendation, not independent | webapp-testing |
| fe-frontend-design | \~180k (repo) | Most-installed skill; avoids generic AI look; official | Aesthetics only, no testing | impeccable |
| fe-impeccable | \~83k | Critique, audit, polish commands; 61 detector rules run without an LLM | 24 commands to learn | frontend-design |
| fe-ccworkflows | \~3.9k | Code, security and design review workflows with GitHub Actions | Only three workflows; design review depends on Playwright MCP | trailofbits, playwright |
| fe-uiuxpromax | \~137k | Big style database | Unverified claims, paid upsell, install friction | frontend-design |

## Writing and research

| ID | Stars | Pros | Cons | Overlaps with |
| --- | --- | --- | --- | --- |
| wr-doc-coauthoring | \~180k (repo) | Three-stage spec and proposal workflow; official | Generic; not tuned to RFC-style writing | AGENTS.md writing rules |
| wr-humanizer | \~58k | Removes 26 AI-writing patterns, keeps meaning; fits your no-em-dash rule | Self-reported blind test; can over-edit on weak patterns | none |
| rs-arxiv | \~3.1k | Reads LaTeX source section by section; BibTeX export | arXiv only | academic-research |
| nt-obsidian | \~50k | Written by Obsidian's CEO; `defuddle` turns web pages into clean Markdown | Useless without Obsidian; slow updates | none |
| rs-academic | \~48k | Full pipeline: research, write, review, integrity checks | CC-BY-NC; reviewer scores uncalibrated; about $4 to 6 per 15k-word paper; hooks only in Claude Code | K-Dense |
| rs-kdense | \~53k | 177 skills incl. database lookups across sciences | Dependency conflicts; weak LaTeX; promotional README | academic-research |

## Electronics, CAD and 3D printing

| ID | Stars | Pros | Cons | Overlaps with |
| --- | --- | --- | --- | --- |
| ee-kicad-mixelpixx | \~2.8k | KiCad 9+: schematics, placement, routing, DRC/ERC, Freerouting, JLCPCB parts | Development moving to an AGPL Rust rewrite for KiCad 10 | kicad-mcp-pro |
| ee-kicad-pro | 136 | Read-only default profile; human approval on release steps; DFM and BOM checks | SI and EMC checks are rough estimates; small | mixelpixx |
| cad-build123d | 59 | Exact solids, STEP export, previews | Very small project | openscad-mcp |
| cad-openscad | 134 | Printability and clearance checks | Mesh output only, no STEP | build123d |
| print-3dprinter | 233 | OctoPrint, Klipper, Bambu, Prusa, Duet; STL edits and slicing | Can start prints on real hardware; Bambu is the only mature backend | none |
| ee-spicebridge | 28 | ngspice, templates, spec checks, KiCad export | Very young | ltspice-mcp |
| ee-ltspice-mcp | 37 | ngspice support, Monte Carlo, sweeps | README warns of breaking changes | spicebridge |

## Gate failures

| ID | Stars | Pros | Cons |
| --- | --- | --- | --- |
| mem-claude-mem | \~102k | Cross-session memory with search | Unauthenticated worker API (#3861); prompt erased when worker dies (#3871); Windows console flashes (#3873); crypto token in README |
| out-caveman | \~103k | Cuts output tokens | Adds 1 to 1.5k input tokens per turn; possible reasoning loss on multi-step work; telemetry on by default |
| rt-ccrouter | \~37k | Routes Claude Code to many providers with fallbacks | 940+ open issues; fallback regressions in v3.1.x; Docker auth token exposed |
