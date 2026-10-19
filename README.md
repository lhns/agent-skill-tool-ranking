# Agent Skill & Tool Ranking

<!-- BEGIN GENERATED: updated -->
Last updated 2026-10-19 · 145 ranked entries, 14 gate failures
<!-- END GENERATED: updated -->

Which agent skills, plugins and MCP servers to use for Pierre's work, ranked with one [rubric](RUBRIC.md). The stack below names one pick per job; the [ranking](ranking/README.md) has every evaluated entry with sub-scores, pros and cons.

## Recommended stack

<!-- BEGIN GENERATED: stack -->
One pick per job, 41 jobs: 2 in use, 4 up next, 1 blocked, 34 planned. Only the jobs loaded globally run in every session; everything else is installed per project. Every pick and alternate links to its repo; the score links to its category ranking.

Status:

- **In use**: adopted after a logged trial, or your own baseline
- **Trying now**: on a 2-week trial with a written exit test; at most 3 at once
- **Up next**: start these first, in table order; move to Trying now when you begin and log the result
- **Blocked**: picked, but a gate check must pass first
- **Planned**: picked for its job; install when you work on that kind of project

| Job | Pick | Status | Score | Load | Setup notes | Alternates |
| --- | --- | --- | --- | --- | --- | --- |
| Workflow | [Your global AGENTS.md](https://github.com/lhns/global-agents-md) | In use | [88](ranking/workflow-and-process.md) | Global | Your baseline; everything else must beat or complement it | none |
| Docker on the remote host | [lhns/remote-docker](https://github.com/lhns/remote-docker) | In use | [88](ranking/self-hosted-infrastructure.md) | Global (CLI) | Your own tool; agents run the real docker and compose CLI through it, so no Docker MCP is needed. For read-only agent access to containers and Swarm, use [L337-org/docker-mcp](https://github.com/L337-org/docker-mcp) instead of the CLI | [L337-org/docker-mcp](https://github.com/L337-org/docker-mcp) (50) |
| Skill install gate | [NVIDIA/SkillSpector](https://github.com/NVIDIA/SkillSpector) | Up next | [69](ranking/agent-safety-and-harness.md) | Before every install | Set it up first so every later install gets scanned. `--no-llm` static mode; sends dependency names to OSV.dev | none |
| Requirements interview | [mattpocock/skills](https://github.com/mattpocock/skills) (grill-with-docs only) | Up next | [71](ranking/workflow-and-process.md) | Global | Install only `grill-with-docs` via `npx skills add` with `DISABLE_TELEMETRY=1`, not the whole plugin | none |
| Scala language intelligence | [Metals MCP](https://scalameta.org/metals/docs/features/mcp/) | Up next | [63](ranking/language-and-library-docs.md) | Scala projects | `cs install metals-mcp`, then `metals-mcp --workspace . --client claude` | [oraios/serena](https://github.com/oraios/serena) (54) |
| Ghidra analysis | [bethington/ghidra-mcp](https://github.com/bethington/ghidra-mcp) | Up next | [58](ranking/reverse-engineering.md) | RE container | Headless, `--lazy`, scripts off, `GHIDRA_MCP_FILE_ROOT` set; the bridge holds the token; Ghidra 12.1.3. Statistical tie with [clearbluejar/pyghidra-mcp](https://github.com/clearbluejar/pyghidra-mcp), which is leaner (18 tools, official Docker image) | [clearbluejar/pyghidra-mcp](https://github.com/clearbluejar/pyghidra-mcp) (60) |
| Multi-tool RE orchestration | [morluto/rea](https://github.com/morluto/rea) | Blocked | [54](ranking/reverse-engineering.md) | RE container | Security gate pending: anomalous stars. Read the code, pin npm `rea-agents`, no secrets, restricted network; own image if its Ghidra 12.1.4 clashes with ghidra-mcp | none |
| RE method knowledge | [wshobson binary-analysis + protocol-RE patterns](https://github.com/wshobson/agents) | Planned | [60](ranking/reverse-engineering.md) | RE container | binary-analysis-patterns and protocol-reverse-engineering; the latter has a Socket warning, read it first | none |
| Android apps | [android-reverse-engineering-skill](https://github.com/SimoneAvogadro/android-reverse-engineering-skill) | Planned | [60](ranking/reverse-engineering.md) | RE container | JDK 17+ and jadx in the image; Linux side only | none |
| Rust, Go, Python language intelligence | [Official LSP plugins](https://github.com/anthropics/claude-plugins-official) (rust-analyzer-lsp, gopls-lsp, pyright-lsp) | Planned | [79](ranking/language-servers-and-language-skills.md) | Per language | rust-analyzer-lsp, gopls-lsp, pyright-lsp; install the language server binaries yourself | [gopls built-in MCP](https://go.dev/gopls/features/mcp) (54) |
| Rust and Go idioms | [wshobson rust-async-patterns](https://github.com/wshobson/agents) | Planned | [60](ranking/language-servers-and-language-skills.md) | Rust projects | Tokio patterns in one file; add a Go skill set only if you write much Go | [samber/cc-skills-golang](https://github.com/samber/cc-skills-golang) (54), [apollographql rust-best-practices](https://github.com/apollographql/skills) (54) |
| Scala library knowledge | [yusufkaraaslan/Skill_Seekers](https://github.com/yusufkaraaslan/Skill_Seekers) | Planned | [54](ranking/building-skills-and-mcps.md) | When needed | Local mode, no API key; generate skills for cats-effect, fs2, http4s, Ox, Magnum | none |
| Scala direct-style conventions | [VirtusLab/scala-skill](https://github.com/VirtusLab/scala-skill) (direct-style-scala) | Planned | [54](ranking/language-servers-and-language-skills.md) | Ox projects only | Never install globally: it auto-loads for any Scala task and would push Ox and sbt 2 into cats-effect repos. Pin a local copy; it fetches chapters from `master` | none |
| Building skills and MCPs | [skill-creator + mcp-builder](https://github.com/anthropics/skills) (+ plugin-dev, mcp-server-dev) | Planned | [73](ranking/building-skills-and-mcps.md) | When needed | skill-creator, mcp-builder, plugin-dev, mcp-server-dev; fits the RE bridge and your own MCPs | none |
| Security review | [official security-guidance + claude-security](https://github.com/anthropics/claude-plugins-official) | Planned | [69](ranking/security-review.md) | Per project | security-guidance and claude-security from the official marketplace; use [trailofbits/skills](https://github.com/trailofbits/skills) for deep audits | [trailofbits/skills](https://github.com/trailofbits/skills) (58) |
| Destructive-command guard | [kenryu42/claude-code-safety-net](https://github.com/kenryu42/claude-code-safety-net) | Planned | [60](ranking/agent-safety-and-harness.md) | Global hook | Pin a version instead of `npx @latest` | [ldayton/Dippy](https://github.com/ldayton/Dippy) (54) |
| Agent config linting | [agent-sh/agnix](https://github.com/agent-sh/agnix) | Planned | [60](ranking/agent-safety-and-harness.md) | When editing AGENTS.md or skills | Rust binary; lints AGENTS.md, SKILL.md, hooks, MCP configs | none |
| Code navigation | [colbymchenry/codegraph](https://github.com/colbymchenry/codegraph) | Planned | [65](ranking/code-intelligence.md) | Per project | `codegraph telemetry off`; keep only if it beats the LSP plugins and Metals in a logged test | [Graphify-Labs/graphify](https://github.com/Graphify-Labs/graphify) (48) |
| Library docs (non-Scala) | [upstash/context7](https://github.com/upstash/context7) | Planned | [60](ranking/language-and-library-docs.md) | Web, Python, Go projects | CLI plus skill mode; Metals covers Scala | none |
| Nix lookup | [utensils/mcp-nixos](https://github.com/utensils/mcp-nixos) | Planned | [67](ranking/self-hosted-infrastructure.md) | Nix and Steam Frame config | Read-only, about 1k tokens | none |
| Infra config generation and validation | [akin-ozer/cc-devops-skills](https://github.com/akin-ozer/cc-devops-skills) | Planned | [60](ranking/self-hosted-infrastructure.md) | Infra repos | Review the validator scripts first | [wshobson infra skills](https://github.com/wshobson/agents) (60) |
| Kubernetes | [containers/kubernetes-mcp-server](https://github.com/containers/kubernetes-mcp-server) | Planned | [63](ranking/kubernetes-and-infrastructure.md) | Infra repos | `--read-only`, dedicated ServiceAccount with narrow RBAC | [Flux159/mcp-server-kubernetes](https://github.com/Flux159/mcp-server-kubernetes) (52) |
| Observability config | [ollygarden/opentelemetry-agent-skills](https://github.com/ollygarden/opentelemetry-agent-skills) | Planned | [60](ranking/observability.md) | Observability repos | Collector, OTTL, semantic conventions | none |
| Metrics queries | [mcp-victoriametrics](https://github.com/VictoriaMetrics-Community/mcp-victoriametrics) | Planned | [56](ranking/observability.md) | Observability repos | Read-only APIs; no client auth, keep it local | [pab1it0/prometheus-mcp-server](https://github.com/pab1it0/prometheus-mcp-server) (54) |
| Parquet and DuckDB | [duckdb/duckdb-skills](https://github.com/duckdb/duckdb-skills) | Planned | [77](ranking/data-and-databases.md) | Db2 archive project | Run on the Linux host; Windows not fully supported | [motherduckdb/mcp-server-motherduck](https://github.com/motherduckdb/mcp-server-motherduck) (54) |
| Postgres | [crystaldba/postgres-mcp](https://github.com/crystaldba/postgres-mcp) | Planned | [54](ranking/data-and-databases.md) | Scheduler project | Restricted mode (read-only, time limit) | [supabase-postgres-best-practices](https://github.com/supabase/agent-skills) (54) |
| Home Assistant | [Home Assistant MCP Server integration](https://www.home-assistant.io/integrations/mcp_server/) | Planned | [56](ranking/home-automation.md) | Home automation | OAuth, only exposed entities, Assist-level control; [homeassistant-ai/ha-mcp](https://github.com/homeassistant-ai/ha-mcp) for power use, [claude-skill-homeassistant](https://github.com/komal-SkyNET/claude-skill-homeassistant) for config work | [homeassistant-ai/ha-mcp](https://github.com/homeassistant-ai/ha-mcp) (52), [claude-skill-homeassistant](https://github.com/komal-SkyNET/claude-skill-homeassistant) (56), [voska/hass-mcp](https://github.com/voska/hass-mcp) (54) |
| Zigbee | [alexpfau/zigbee2mqtt-mcp](https://github.com/alexpfau/zigbee2mqtt-mcp) | Planned | [60](ranking/home-automation.md) | Home automation | Use the safe write tier; it can still actuate locks and sirens | none |
| ABAP | [oisee/vibing-steampunk](https://github.com/oisee/vibing-steampunk) | Planned | [60](ranking/sap-and-abap.md) | SAP work | `--read-only` plus package allowlist | [mario-andreschak/mcp-abap-adt](https://github.com/mario-andreschak/mcp-abap-adt) (52) |
| Web design | [anthropics frontend-design](https://github.com/anthropics/skills) | Planned | [73](ranking/web-frontend-and-testing.md) | Web projects | Official | [pbakaus/impeccable](https://github.com/pbakaus/impeccable) (54) |
| Web testing | [anthropics webapp-testing](https://github.com/anthropics/skills) | Planned | [71](ranking/web-frontend-and-testing.md) | Web projects | Official; uses Playwright. Tie with [microsoft/playwright-cli](https://github.com/microsoft/playwright-cli) | [microsoft/playwright-cli](https://github.com/microsoft/playwright-cli) (69) |
| Technical writing | [anthropics doc-coauthoring](https://github.com/anthropics/skills) | Planned | [60](ranking/writing-and-research.md) | Writing projects | Structure and drafting | none |
| Prose cleanup | [blader/humanizer](https://github.com/blader/humanizer) | Planned | [60](ranking/writing-and-research.md) | Writing projects | Finished docs only | [vercel writing-guidelines](https://github.com/vercel-labs/agent-skills) (60) |
| Web search | [ihor-sokoliuk/mcp-searxng](https://github.com/ihor-sokoliuk/mcp-searxng) | Planned | [60](ranking/writing-and-research.md) | Research projects | Needs your own SearXNG; blocks private URLs | [kagisearch/kagimcp](https://github.com/kagisearch/kagimcp) (54) |
| Papers | [academic-research-skills](https://github.com/Imbad0202/academic-research-skills) | Planned | [50](ranking/writing-and-research.md) | Research projects | CC-BY-NC; about $4 to 6 per long paper | none |
| Paper lookup | [blazickjp/arxiv-mcp-server](https://github.com/blazickjp/arxiv-mcp-server) | Planned | [56](ranking/writing-and-research.md) | Research projects | BibTeX export | none |
| PCB review and simulation | [aklofas/kicad-happy](https://github.com/aklofas/kicad-happy) (review, EMC, SPICE, BOM) | Planned | [67](ranking/electronics-cad-and-3d-printing.md) | KiCad projects | DigiKey and Mouser keys optional; Windows symlinks need Developer Mode | [clanker-lover/spicebridge](https://github.com/clanker-lover/spicebridge) (52), [cognitohazard/ltspice-mcp](https://github.com/cognitohazard/ltspice-mcp) (52) |
| PCB editing | [mixelpixx/KiCAD-MCP-Server](https://github.com/mixelpixx/KiCAD-MCP-Server) (editing) | Planned | [56](ranking/electronics-cad-and-3d-printing.md) | KiCad projects | Work on a git-tracked copy | [oaslananka/kicad-mcp-pro](https://github.com/oaslananka/kicad-mcp-pro) (54) |
| Firmware boards | [alexex1993/mcu-skills](https://github.com/alexex1993/mcu-skills) | Planned | [58](ranking/electronics-cad-and-3d-printing.md) | Firmware projects | ESP32, STM32, RP2040, nRF, AVR | none |
| CAD for printing | [pzfreo/build123d-mcp](https://github.com/pzfreo/build123d-mcp) | Planned | [56](ranking/electronics-cad-and-3d-printing.md) | CAD projects | STEP export | [RobertCoop/openscad-mcp](https://github.com/RobertCoop/openscad-mcp) (54) |
| Printer control | [mcp-3D-printer-server](https://github.com/DMontgomery40/mcp-3D-printer-server) | Planned | [52](ranking/electronics-cad-and-3d-printing.md) | Printer projects | Never let it start a print without your confirmation | none |

**Jobs with no pick yet:** Proxmox (only immature servers: [infrastructure-mcp](https://github.com/radumalica/infrastructure-mcp) has 5 stars, [Proximo](https://github.com/john-broadway/proximo) exposes 924 tools), Ceph ([AIops-tools/Ceph-AIops](https://github.com/AIops-tools/Ceph-AIops) has 0 stars and looks generated), Docker Swarm ([L337-org/docker-mcp](https://github.com/L337-org/docker-mcp) has 9 stars), Stalwart and S3/MinIO. No cats-effect, fs2, http4s or Circe skill exists; generate them with [yusufkaraaslan/Skill_Seekers](https://github.com/yusufkaraaslan/Skill_Seekers).
<!-- END GENERATED: stack -->

## Index

- [How to use this repo](HOW-TO-USE.md)
- [Agent instructions](AGENTS.md): how agents add, score and re-rank entries
- [Rubric](RUBRIC.md): gates, criteria, evidence levels, statuses, consistency rules, re-rank protocol, pitfalls
- [Ranking](ranking/README.md), by category:
<!-- BEGIN GENERATED: categories -->
  - [Workflow and process](ranking/workflow-and-process.md)
  - [Code intelligence](ranking/code-intelligence.md)
  - [Language and library docs](ranking/language-and-library-docs.md)
  - [Reverse engineering](ranking/reverse-engineering.md)
  - [Security review](ranking/security-review.md)
  - [Kubernetes and infrastructure](ranking/kubernetes-and-infrastructure.md)
  - [Web frontend and testing](ranking/web-frontend-and-testing.md)
  - [Writing and research](ranking/writing-and-research.md)
  - [Electronics, CAD and 3D printing](ranking/electronics-cad-and-3d-printing.md)
  - [Language servers and language skills](ranking/language-servers-and-language-skills.md)
  - [Self-hosted infrastructure](ranking/self-hosted-infrastructure.md)
  - [Observability](ranking/observability.md)
  - [Data and databases](ranking/data-and-databases.md)
  - [Home automation](ranking/home-automation.md)
  - [SAP and ABAP](ranking/sap-and-abap.md)
  - [Agent safety and harness](ranking/agent-safety-and-harness.md)
  - [Building skills and MCPs](ranking/building-skills-and-mcps.md)
  - [Architecture](ranking/architecture.md)
  - [Listed, not ranked (gate failure)](ranking/listed-not-ranked-gate-failure.md)
<!-- END GENERATED: categories -->
- [Pros and cons](PROS-AND-CONS.md)
- [Experience log](EXPERIENCE-LOG.md)
- [Discovery sources](DISCOVERY-SOURCES.md)
- [Inbox and watchlist](INBOX-AND-WATCHLIST.md)
- [Changelog](CHANGELOG.md)
- Data: [entries](data/entries.toml), [categories](data/categories.toml), [stack](data/stack.toml). Tables are generated by `python scripts/build.py`.

Originally exported from the [Claude Doc "Agent Skill & Tool Ranking"](https://claude.ai/artifact/RGeG2iQ57S3Y5471XzwWus) on 2026-10-19. This repo is now the source of truth; the Claude Doc is no longer updated.
