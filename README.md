# Agent Skill & Tool Ranking

2026-10-19 · Pierre

## Recommended stack

One pick per job. Only your AGENTS.md, one interview skill and a safety hook load in every session; everything else is per project. The first three trials are Metals MCP, grill-with-docs and ghidra-mcp; the rest wait in the queue until a slot frees up.

| Job | Pick | Status | Load | Setup notes | Alternate |
| --- | --- | --- | --- | --- | --- |
| Workflow | Your AGENTS.md | Baseline | Global | Already installed | none |
| Requirements interview | mattpocock `grill-with-docs` | Trial 1 | Global | Install only this skill via `npx skills add` (set `DISABLE_TELEMETRY=1`), not the plugin | superpowers brainstorm |
| Scala language intelligence | Metals MCP | Trial 2 | Scala projects | `cs install metals-mcp`, then `metals-mcp --workspace . --client claude` | serena |
| Ghidra analysis | bethington/ghidra-mcp | Trial 3 | RE container | Headless, `--lazy`, scripts off, `GHIDRA_MCP_FILE_ROOT` set; bridge holds the token; Ghidra 12.1.3 | pyghidra-mcp (leaner, tie) |
| Skill install gate | NVIDIA SkillSpector | Queued, next | Run before every install | `--no-llm` static mode; note it sends dependency names to OSV.dev | getsentry skill-scanner |
| Rust, Go, Python language intelligence | Official LSP plugins (rust-analyzer-lsp, gopls-lsp, pyright-lsp) | Queued | Per language | Install the language server binaries yourself | gopls built-in MCP |
| Scala library knowledge | Skill\_Seekers | Queued | When needed | Local mode, no API key; generate skills for cats-effect, fs2, http4s, Ox, Magnum | Context7 |
| Scala direct-style conventions | VirtusLab `scala-skill` (direct-style-scala) | Queued | Ox projects only | Install per project, never globally: it auto-loads for any Scala task and would push Ox and sbt 2 into cats-effect repos; pin a local copy, since it fetches chapters from `master` | none |
| Building skills and MCPs | Official skill-creator + mcp-builder | Queued | When needed | Fits the RE bridge and your own MCPs | none |
| Multi-tool RE orchestration | REA | Gate pending | RE container | Read the code, pin npm `rea-agents`, no secrets, restricted network; own image if Ghidra pins clash | none |
| RE method knowledge | wshobson binary-analysis-patterns, protocol-reverse-engineering | Queued | RE container | protocol-RE has a Socket warning; read first | sickn33 reverse-engineer |
| Android apps | android-reverse-engineering skill | Queued | RE container | JDK 17+ and jadx in the image | REA JADX backend |
| Security review | Official security-guidance + claude-security | Queued | Per project | Official marketplace | trailofbits/skills for deep audits |
| Destructive-command guard | claude-code-safety-net | Queued | Global hook | Pin a version instead of `npx @latest` | Dippy |
| Agent config linting | agnix | Queued | When editing AGENTS.md or skills | Rust binary; lints AGENTS.md, SKILL.md, hooks | none |
| Code navigation | codegraph | Queued | Per project | `codegraph telemetry off`; keep only if it beats LSP plugins and Metals in a logged test | graphify |
| Library docs (non-Scala) | Context7 | Queued | Web, Python, Go projects | CLI plus skill mode | none |
| Nix lookup | mcp-nixos | Queued | Nix and Steam Frame config | Read-only, about 1k tokens | none |
| Infra config generation and validation | cc-devops-skills | Queued | Infra repos | Review the validator scripts first | wshobson infra skills |
| Docker on the remote host | ckreiling/mcp-server-docker | Queued | Infra repos | `DOCKER_HOST=ssh://`; no read-only mode, so use a limited user | L337-org/docker-mcp for Swarm |
| Kubernetes | containers/kubernetes-mcp-server | Queued | Infra repos | `--read-only`, dedicated ServiceAccount with narrow RBAC | Flux159 server |
| Observability config | ollygarden OpenTelemetry skills | Queued | Observability repos | Collector, OTTL, semantic conventions | otelcol-doctor |
| Metrics queries | mcp-victoriametrics | Queued | Observability repos | Read-only APIs; no client auth, keep it local | prometheus-mcp-server |
| Parquet and DuckDB | duckdb/duckdb-skills | Queued | Db2 archive project | Run on the Linux host; Windows not fully supported | MotherDuck MCP |
| Postgres | crystaldba/postgres-mcp | Queued | Scheduler project | Restricted mode (read-only, time limit) | supabase pg best practices |
| Home Assistant | Official HA MCP Server integration | Queued | Home automation | OAuth, only exposed entities, Assist-level control | ha-mcp for power use |
| Zigbee | zigbee2mqtt-mcp | Queued | Home automation | "safe" write tier; it can still actuate locks and sirens | none |
| ABAP | vibing-steampunk | Queued | SAP work | `--read-only` plus package allowlist | mcp-abap-adt (read-only) |
| Web design | anthropics `frontend-design` | Queued | Web projects | Official | impeccable |
| Web testing | anthropics `webapp-testing` | Queued | Web projects | Official; uses Playwright | playwright-cli (tie) |
| Technical writing | anthropics `doc-coauthoring` | Queued | Writing projects | Structure and drafting | none |
| Prose cleanup | humanizer | Queued | Writing projects | Finished docs only | vercel writing-guidelines |
| Web search | mcp-searxng | Queued | Research projects | Needs your own SearXNG; blocks private URLs | kagimcp (paid) |
| Papers | academic-research-skills | Queued | Research projects | CC-BY-NC; about $4 to 6 per long paper | K-Dense |
| Paper lookup | arxiv-mcp-server | Queued | Research projects | BibTeX export | paper-search-mcp |
| PCB review and simulation | kicad-happy | Queued | KiCad projects | DigiKey/Mouser keys optional; Windows symlinks need Developer Mode | spicebridge |
| PCB editing | mixelpixx/KiCAD-MCP-Server | Queued | KiCad projects | Work on a git-tracked copy | kicad-mcp-pro |
| Firmware boards | mcu-skills | Queued | Firmware projects | ESP32, STM32, RP2040, nRF, AVR | none |
| CAD for printing | build123d-mcp | Queued | CAD projects | STEP export | openscad-mcp |
| Printer control | mcp-3D-printer-server | Queued | Printer projects | Never start a print without confirmation | none |

**Jobs with no pick yet:** Proxmox (only immature servers: infrastructure-mcp has 5 stars, Proximo exposes 924 tools), Ceph (one 0-star server that looks generated), Docker Swarm (one 9-star server), Stalwart and S3/MinIO. No cats-effect, fs2, http4s or Circe skill exists; generate them with Skill\_Seekers. Direct style (Ox, Magnum, Tapir) is covered by VirtusLab's scala-skill.


## Index

- [How to use this repo](HOW-TO-USE.md)
- [Agent instructions](AGENTS.md): how agents add, score and re-rank entries
- [Rubric](RUBRIC.md): gates, criteria, evidence levels, statuses, consistency rules, re-rank protocol, pitfalls
- [Ranking](ranking/README.md) (generated from `data/`)
  - [Workflow and process](ranking/workflow-and-process.md)
  - [Code intelligence](ranking/code-intelligence.md)
  - [Language and library docs](ranking/language-and-library-docs.md)
  - [Reverse engineering](ranking/reverse-engineering.md)
  - [Security review](ranking/security-review.md)
  - [Kubernetes and infrastructure](ranking/kubernetes-and-infrastructure.md)
  - [Web frontend and testing](ranking/web-frontend-and-testing.md)
  - [Writing and research](ranking/writing-and-research.md)
  - [Electronics, CAD and 3D printing](ranking/electronics-cad-and-3d-printing.md)
  - [Listed, not ranked (gate failure)](ranking/listed-not-ranked-gate-failure.md)
  - [Language servers and language skills](ranking/language-servers-and-language-skills.md)
  - [Self-hosted infrastructure](ranking/self-hosted-infrastructure.md)
  - [Observability](ranking/observability.md)
  - [Data and databases](ranking/data-and-databases.md)
  - [Home automation](ranking/home-automation.md)
  - [SAP and ABAP](ranking/sap-and-abap.md)
  - [Agent safety and harness](ranking/agent-safety-and-harness.md)
  - [Building skills and MCPs](ranking/building-skills-and-mcps.md)
  - [Architecture](ranking/architecture.md)
- [Pros and cons](PROS-AND-CONS.md) (generated)
- Data: [entries](data/entries.toml), [categories](data/categories.toml); build with `python scripts/build.py`
- [Experience log](EXPERIENCE-LOG.md)
- [Discovery sources](DISCOVERY-SOURCES.md)
- [Inbox and watchlist](INBOX-AND-WATCHLIST.md)
- [Changelog](CHANGELOG.md)

Originally exported from the [Claude Doc "Agent Skill & Tool Ranking"](https://claude.ai/artifact/RGeG2iQ57S3Y5471XzwWus) on 2026-10-19. This repo is now the source of truth; the Claude Doc is no longer updated.
