# Agent Skill & Tool Ranking

<!-- BEGIN GENERATED: updated -->
Last updated 2026-11-13 · 189 evaluated entries, 3 tested hands-on, 15 gate failures
<!-- END GENERATED: updated -->

Which agent skills, plugins and MCP servers to use for Pierre's work, triaged with one [rubric](RUBRIC.md). The stack below names one default per job; the [ranking](ranking/README.md) has every evaluated entry with its tier, pros and cons. Only entries tested hands-on carry a score; everything else is a judged shortlist, not a measurement.

## Recommended stack

<!-- BEGIN GENERATED: stack -->
One pick per job, 43 jobs: 3 in use, 3 trying now, 1 up next, 1 blocked, 35 planned. A pick is the default to try for that job, not a proven winner: only entries marked with a score have been tested hands-on. Only the jobs loaded globally run in every session; everything else is installed per project. All candidates for a job are in [ranking/by-job.md](ranking/by-job.md).

Status:

- **In use**: adopted after a logged trial, or your own baseline
- **Trying now**: on a 2-week trial with a written exit test; at most 3 at once
- **Up next**: start these first, in table order; move to Trying now when you begin and log the result
- **Blocked**: picked, but a gate check must pass first
- **Planned**: picked for its job; install when you work on that kind of project

| Job | Pick | Status | Evidence | Load | Setup notes | Alternates |
| --- | --- | --- | --- | --- | --- | --- |
| Workflow | [Your global AGENTS.md](https://github.com/lhns/global-agents-md) | In use | [E3, own, score 88](ranking/workflow-and-process.md) | Global | Your baseline; everything else must beat or complement it | none |
| Run agents isolated | [lhns/agent-workspace](https://github.com/lhns/agent-workspace) | In use | [E3, own, score 83](ranking/agent-safety-and-harness.md) | Global (launcher) | Your own tool; agents see only the workspace and their own state. Still shared with every agent: the whole `.env`, the git token and the remote-docker seed key, and there is no egress policy. For VM isolation and egress control use [discobox-ai/discobox](https://github.com/discobox-ai/discobox) | [discobox-ai/discobox](https://github.com/discobox-ai/discobox), [inoio/agents-sandbox](https://github.com/inoio/agents-sandbox) |
| Docker on the remote host | [lhns/remote-docker](https://github.com/lhns/remote-docker) | In use | [E3, own, score 88](ranking/self-hosted-infrastructure.md) | Global (CLI) | Your own tool; agents run the real docker and compose CLI through it, so no Docker MCP is needed. For read-only agent access to containers and Swarm, use [L337-org/docker-mcp](https://github.com/L337-org/docker-mcp) instead of the CLI | [L337-org/docker-mcp](https://github.com/L337-org/docker-mcp) |
| Skill install gate | [NVIDIA/SkillSpector](https://github.com/NVIDIA/SkillSpector) | Trying now | [E1, untested](ranking/agent-safety-and-harness.md) | Before every install | Set it up first so every later install gets scanned. `--no-llm` static mode; sends dependency names to OSV.dev **Trial until 2026-11-27.** Exit test: Scan the next 5 skills or plugins you install. Keep it if it runs on your setup without manual fixes and no false alarm costs you more than 5 minutes; drop it if it misses a problem you find by reading. | none |
| Requirements interview | [mattpocock/skills](https://github.com/mattpocock/skills) (grill-with-docs only) | Trying now | [E1, untested](ranking/workflow-and-process.md) | Global | Install only `grill-with-docs` via `npx skills add` with `DISABLE_TELEMETRY=1`, not the whole plugin **Trial until 2026-11-27.** Exit test: Use grill-with-docs on 3 features. Keep it if at least 2 interviews surface a requirement or decision you had not written down and its glossary and ADR output needs under 10 minutes of cleanup each. | none |
| Scala language intelligence | [Metals MCP](https://scalameta.org/metals/docs/features/mcp/) | Trying now | [E1, official, untested](ranking/language-and-library-docs.md) | Scala projects | `cs install metals-mcp`, then `metals-mcp --workspace . --client claude` **Trial until 2026-11-27.** Exit test: Do 5 comparable tasks in a cats-effect repo with it and count compile-fix round trips against 5 without it. Keep it if the count drops and Metals indexing never blocks a session. | [oraios/serena](https://github.com/oraios/serena) |
| Ghidra analysis | [bethington/ghidra-mcp](https://github.com/bethington/ghidra-mcp) | Up next | [E1, untested](ranking/reverse-engineering.md) | RE container | Headless, `--lazy`, scripts off, `GHIDRA_MCP_FILE_ROOT` set; the bridge holds the token; Ghidra 12.1.3. Statistical tie with [clearbluejar/pyghidra-mcp](https://github.com/clearbluejar/pyghidra-mcp), which is leaner (18 tools, official Docker image) | [clearbluejar/pyghidra-mcp](https://github.com/clearbluejar/pyghidra-mcp) |
| Multi-tool RE orchestration | [morluto/rea](https://github.com/morluto/rea) | Blocked | [E0, untested](ranking/reverse-engineering.md) | RE container | Security gate pending: anomalous stars. Read the code, pin npm `rea-agents`, no secrets, restricted network; own image if its Ghidra 12.1.4 clashes with ghidra-mcp | none |
| RE method knowledge | [wshobson binary-analysis + protocol-RE patterns](https://github.com/wshobson/agents) | Planned | [E1, untested](ranking/reverse-engineering.md) | RE container | binary-analysis-patterns and protocol-reverse-engineering; the latter has a Socket warning, read it first | none |
| Android apps | [android-reverse-engineering-skill](https://github.com/SimoneAvogadro/android-reverse-engineering-skill) | Planned | [E1, untested](ranking/reverse-engineering.md) | RE container | JDK 17+ and jadx in the image; Linux side only | none |
| Rust, Go, Python language intelligence | [Official LSP plugins](https://github.com/anthropics/claude-plugins-official) (rust-analyzer-lsp, gopls-lsp, pyright-lsp) | Planned | [E1, official, untested](ranking/language-servers-and-language-skills.md) | Per language | rust-analyzer-lsp, gopls-lsp, pyright-lsp; install the language server binaries yourself | [gopls built-in MCP](https://go.dev/gopls/features/mcp) |
| Rust and Go idioms | [wshobson rust-async-patterns](https://github.com/wshobson/agents) | Planned | [E1, untested](ranking/language-servers-and-language-skills.md) | Rust projects | Tokio patterns in one file; add a Go skill set only if you write much Go | [samber/cc-skills-golang](https://github.com/samber/cc-skills-golang), [apollographql rust-best-practices](https://github.com/apollographql/skills) |
| Scala library knowledge | [yusufkaraaslan/Skill_Seekers](https://github.com/yusufkaraaslan/Skill_Seekers) | Planned | [E1, untested](ranking/building-skills-and-mcps.md) | When needed | Local mode, no API key; generate skills for cats-effect, fs2, http4s, Ox, Magnum | none |
| Scala direct-style conventions | [VirtusLab/scala-skill](https://github.com/VirtusLab/scala-skill) (direct-style-scala) | Planned | [E1, untested](ranking/language-servers-and-language-skills.md) | Ox projects only | Never install globally: it auto-loads for any Scala task and would push Ox and sbt 2 into cats-effect repos. Pin a local copy; it fetches chapters from `master` | none |
| Building skills and MCPs | [skill-creator + mcp-builder](https://github.com/anthropics/skills) (+ plugin-dev, mcp-server-dev) | Planned | [E1, official, untested](ranking/building-skills-and-mcps.md) | When needed | skill-creator, mcp-builder, plugin-dev, mcp-server-dev; fits the RE bridge and your own MCPs | none |
| Security review | [official security-guidance + claude-security](https://github.com/anthropics/claude-plugins-official) | Planned | [E1, official, untested](ranking/security-review.md) | Per project | security-guidance and claude-security from the official marketplace; use [trailofbits/skills](https://github.com/trailofbits/skills) for deep audits | [trailofbits/skills](https://github.com/trailofbits/skills) |
| Destructive-command guard | [kenryu42/claude-code-safety-net](https://github.com/kenryu42/claude-code-safety-net) | Planned | [E1, untested](ranking/agent-safety-and-harness.md) | Global hook | Pin a version instead of `npx @latest` | [ldayton/Dippy](https://github.com/ldayton/Dippy) |
| Agent config linting | [agent-sh/agnix](https://github.com/agent-sh/agnix) | Planned | [E0, untested](ranking/agent-safety-and-harness.md) | When editing AGENTS.md or skills | Rust binary; lints AGENTS.md, SKILL.md, hooks, MCP configs | none |
| Code navigation | [colbymchenry/codegraph](https://github.com/colbymchenry/codegraph) | Planned | [E1, untested](ranking/code-intelligence.md) | Per project | `codegraph telemetry off`; keep only if it beats the LSP plugins and Metals in a logged test | [Graphify-Labs/graphify](https://github.com/Graphify-Labs/graphify) |
| Library docs (non-Scala) | [upstash/context7](https://github.com/upstash/context7) | Planned | [E1, untested](ranking/language-and-library-docs.md) | Web, Python, Go projects | CLI plus skill mode; Metals covers Scala | none |
| Nix lookup | [utensils/mcp-nixos](https://github.com/utensils/mcp-nixos) | Planned | [E1, untested](ranking/self-hosted-infrastructure.md) | Nix and Steam Frame config | Read-only, about 1k tokens | none |
| Infra config generation and validation | [akin-ozer/cc-devops-skills](https://github.com/akin-ozer/cc-devops-skills) | Planned | [E0, untested](ranking/self-hosted-infrastructure.md) | Infra repos | Review the validator scripts first | [wshobson infra skills](https://github.com/wshobson/agents) |
| Kubernetes | [containers/kubernetes-mcp-server](https://github.com/containers/kubernetes-mcp-server) | Planned | [E1, untested](ranking/kubernetes-and-infrastructure.md) | Infra repos | `--read-only`, dedicated ServiceAccount with narrow RBAC | [Flux159/mcp-server-kubernetes](https://github.com/Flux159/mcp-server-kubernetes) |
| Observability config | [ollygarden/opentelemetry-agent-skills](https://github.com/ollygarden/opentelemetry-agent-skills) | Planned | [E0, untested](ranking/observability.md) | Observability repos | Collector, OTTL, semantic conventions | none |
| Metrics queries | [mcp-victoriametrics](https://github.com/VictoriaMetrics-Community/mcp-victoriametrics) | Planned | [E1, untested](ranking/observability.md) | Observability repos | Read-only APIs; no client auth, keep it local | [pab1it0/prometheus-mcp-server](https://github.com/pab1it0/prometheus-mcp-server) |
| Parquet and DuckDB | [duckdb/duckdb-skills](https://github.com/duckdb/duckdb-skills) | Planned | [E1, official, untested](ranking/data-and-databases.md) | Db2 archive project | Run on the Linux host; Windows not fully supported | [motherduckdb/mcp-server-motherduck](https://github.com/motherduckdb/mcp-server-motherduck) |
| Postgres | [crystaldba/postgres-mcp](https://github.com/crystaldba/postgres-mcp) | Planned | [E1, untested](ranking/data-and-databases.md) | Scheduler project | Restricted mode (read-only, time limit) | [supabase-postgres-best-practices](https://github.com/supabase/agent-skills) |
| Home Assistant | [Home Assistant MCP Server integration](https://www.home-assistant.io/integrations/mcp_server/) | Planned | [E1, official, untested](ranking/home-automation.md) | Home automation | OAuth, only exposed entities, Assist-level control; [homeassistant-ai/ha-mcp](https://github.com/homeassistant-ai/ha-mcp) for power use, [claude-skill-homeassistant](https://github.com/komal-SkyNET/claude-skill-homeassistant) for config work | [homeassistant-ai/ha-mcp](https://github.com/homeassistant-ai/ha-mcp), [claude-skill-homeassistant](https://github.com/komal-SkyNET/claude-skill-homeassistant), [voska/hass-mcp](https://github.com/voska/hass-mcp) |
| Zigbee | [alexpfau/zigbee2mqtt-mcp](https://github.com/alexpfau/zigbee2mqtt-mcp) | Planned | [E0, untested](ranking/home-automation.md) | Home automation | Use the safe write tier; it can still actuate locks and sirens | none |
| ABAP | [oisee/vibing-steampunk](https://github.com/oisee/vibing-steampunk) | Planned | [E1, untested](ranking/sap-and-abap.md) | SAP work | `--read-only` plus package allowlist | [mario-andreschak/mcp-abap-adt](https://github.com/mario-andreschak/mcp-abap-adt) |
| Web design | [anthropics frontend-design](https://github.com/anthropics/skills) | Planned | [E1, official, untested](ranking/web-frontend-and-testing.md) | Web projects | Official | [pbakaus/impeccable](https://github.com/pbakaus/impeccable) |
| Web testing | [anthropics webapp-testing](https://github.com/anthropics/skills) | Planned | [E1, official, untested](ranking/web-frontend-and-testing.md) | Web projects | Official; uses Playwright. Tie with [microsoft/playwright-cli](https://github.com/microsoft/playwright-cli) | [microsoft/playwright-cli](https://github.com/microsoft/playwright-cli) |
| Technical writing | [anthropics doc-coauthoring](https://github.com/anthropics/skills) | Planned | [E1, official, untested](ranking/writing-and-research.md) | Writing projects | Structure and drafting | none |
| Docs and ADR diagrams | [cathrynlavery/diagram-design](https://github.com/cathrynlavery/diagram-design) | Planned | [E1, untested](ranking/writing-and-research.md) | Writing projects | Self-contained HTML+SVG per diagram; remove the Google Fonts link if you publish offline | [muthuishere/hand-drawn-diagrams](https://github.com/muthuishere/hand-drawn-diagrams) |
| Prose cleanup | [blader/humanizer](https://github.com/blader/humanizer) | Planned | [E1, untested](ranking/writing-and-research.md) | Writing projects | Finished docs only | [vercel writing-guidelines](https://github.com/vercel-labs/agent-skills) |
| Web search | [ihor-sokoliuk/mcp-searxng](https://github.com/ihor-sokoliuk/mcp-searxng) | Planned | [E1, untested](ranking/writing-and-research.md) | Research projects | Needs your own SearXNG; blocks private URLs | [kagisearch/kagimcp](https://github.com/kagisearch/kagimcp) |
| Papers | [academic-research-skills](https://github.com/Imbad0202/academic-research-skills) | Planned | [E1, untested](ranking/writing-and-research.md) | Research projects | CC-BY-NC; about $4 to 6 per long paper | none |
| Paper lookup | [blazickjp/arxiv-mcp-server](https://github.com/blazickjp/arxiv-mcp-server) | Planned | [E1, untested](ranking/writing-and-research.md) | Research projects | BibTeX export | none |
| PCB review and simulation | [aklofas/kicad-happy](https://github.com/aklofas/kicad-happy) (review, EMC, SPICE, BOM) | Planned | [E1, untested](ranking/electronics-cad-and-3d-printing.md) | KiCad projects | DigiKey and Mouser keys optional; Windows symlinks need Developer Mode | [clanker-lover/spicebridge](https://github.com/clanker-lover/spicebridge), [cognitohazard/ltspice-mcp](https://github.com/cognitohazard/ltspice-mcp) |
| PCB editing | [mixelpixx/KiCAD-MCP-Server](https://github.com/mixelpixx/KiCAD-MCP-Server) (editing) | Planned | [E1, untested](ranking/electronics-cad-and-3d-printing.md) | KiCad projects | Work on a git-tracked copy | [oaslananka/kicad-mcp-pro](https://github.com/oaslananka/kicad-mcp-pro) |
| Firmware boards | [alexex1993/mcu-skills](https://github.com/alexex1993/mcu-skills) | Planned | [E0, untested](ranking/electronics-cad-and-3d-printing.md) | Firmware projects | ESP32, STM32, RP2040, nRF, AVR | none |
| CAD for printing | [pzfreo/build123d-mcp](https://github.com/pzfreo/build123d-mcp) | Planned | [E1, untested](ranking/electronics-cad-and-3d-printing.md) | CAD projects | STEP export | [earthtojake/text-to-cad](https://github.com/earthtojake/text-to-cad), [RobertCoop/openscad-mcp](https://github.com/RobertCoop/openscad-mcp) |
| Printer control | [mcp-3D-printer-server](https://github.com/DMontgomery40/mcp-3D-printer-server) | Planned | [E1, untested](ranking/electronics-cad-and-3d-printing.md) | Printer projects | Never let it start a print without your confirmation | none |

**Jobs with no pick yet:** Proxmox (only immature servers: [infrastructure-mcp](https://github.com/radumalica/infrastructure-mcp) has 5 stars, [Proximo](https://github.com/john-broadway/proximo) exposes 924 tools), Ceph ([AIops-tools/Ceph-AIops](https://github.com/AIops-tools/Ceph-AIops) has 0 stars and looks generated), Docker Swarm ([L337-org/docker-mcp](https://github.com/L337-org/docker-mcp) has 9 stars), Stalwart and S3/MinIO. No cats-effect, fs2, http4s or Circe skill exists; generate them with [yusufkaraaslan/Skill_Seekers](https://github.com/yusufkaraaslan/Skill_Seekers).
<!-- END GENERATED: stack -->

## Index

- [How to use this repo](HOW-TO-USE.md)
- [Agent instructions](AGENTS.md): how agents add, score and re-rank entries
- [Rubric](RUBRIC.md): gates, Fit, tiers, evidence, trust and review depth, trials before intake, rater noise, pitfalls
- [Ranking](ranking/README.md), per job and by category:
<!-- BEGIN GENERATED: categories -->
  - [Candidates per job](ranking/by-job.md)
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
  - [Memory and context](ranking/memory-and-context.md)
  - [Harness plugins](ranking/harness-plugins.md)
  - [Local models](ranking/local-models.md)
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
