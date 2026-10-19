## Second pass: entries from the 10 discovery sources

| ID | Stars | Pros | Cons |
| --- | --- | --- | --- |
| lang-lsp-official | 40k (marketplace) | Official; real compiler diagnostics and references for Rust, Go, Python | You install the language servers; no Scala plugin exists |
| lang-rust-async | 41k (repo) | Tokio JoinSet, select!, cancellation, tracing in one file; audits pass | Part of a huge mixed-quality repo |
| lang-go-samber | 3.3k | Strongest Go set; write, review and audit modes | Audit mode spawns up to 5 subagents |
| lang-serena | 27.9k | LSP-backed editing in 40+ languages incl. Scala and Nix | Many tools; includes shell execution |
| lang-gopls-mcp | n/a (gopls) | Official Go team, attaches to the live session | Experimental; overlaps the LSP plugin |
| lang-rust-apollo | 101 | Apollo's internal Rust handbook | Marked experimental |
| lang-bash-defensive | 41k (repo) | Production Bash patterns; audits pass | Generic |
| lang-warp-fix-errors | 540 | Fixes Rust compile and Clippy errors; skill-doctor grades skills | Audits unverified |
| lang-go-eduardo | 76 | Declares allowed-tools; review skills can't write | Low adoption |
| lang-mcp-lsp-bridge | 1.6k | Any stdio LSP over MCP | Beta; Windows not mentioned |
| lang-rust-actionbook | 1.5k | Layered Rust reasoning | Needs its own MCP server |
| lang-agent-lsp | 98 | Speculative edits, 30 languages incl. Scala | 65 tools; one maintainer |
| infra-mcp-nixos | 823 | Packages, options, Home Manager; works on Windows; read-only; \~1k tokens | Store and flake actions need Nix |
| infra-cc-devops | 306 | Validators actually lint and dry-run: k8s, Helm, Dockerfile, PromQL | Runs local scripts; 24 commits |
| infra-wshobson | 41k (repo) | Helm, manifests, GitOps, Grafana dashboards | Audits only verified for grafana-dashboards |
| infra-gateway-radumalica | 5 | One safe gateway: read-only default, dry-run, token on HTTP | Unproven |
| infra-docker-ckreiling | 736 | Works with `DOCKER_HOST=ssh://` | No read-only mode; no Swarm |
| infra-docker-expert | 47.9k (repo) | Inspects before acting; audits pass | Aggregator repo of 2,700 skills |
| infra-docker-l337 | 9 | Only real Swarm coverage; read-only and no-destructive modes | Python 3.14+; 150+ tools |
| infra-github-mcp | 32.2k | Official; toolsets and read-only flag | `gh` CLI is cheaper in tokens |
| infra-hashicorp | 761 | Official Terraform and Packer | You don't use Terraform |
| infra-mcp-gateway | 1.5k | Runs MCP servers in isolated containers | Built around Docker Desktop |
| infra-mirrord | 21 | Runs local code inside a live cluster | Tied to mirrord |
| infra-proximo | 54 | Read-only default, plan-then-confirm, audit log | 924 tools |
| infra-mcp-proxmox | 16 | Two-step confirm on destructive ops | No read-only mode |
| infra-portainer | 225 | Official, read-only option | Needs Portainer |
| obs-otel-skills | 83 | Vendor-neutral Collector, OTTL, semconv; 211 commits | No Rust or Scala SDK skill |
| obs-victoriametrics | 238 | Covers almost all read-only VM APIs, relabel and rules debuggers | No client auth; embedded docs DB costs resources |
| obs-prometheus | 515 | 6 tools, mTLS | VictoriaMetrics compatibility unstated |
| obs-otelcol-doctor | 8 | Validates via `otelcol validate` | Tiny |
| obs-grafana | 3.3k | Official, `--disable-write` | Large tool surface |
| data-duckdb | 572 | Official; Parquet local or remote; DuckDB docs search | Windows not fully supported |
| data-postgres-pro | 3.2k | Restricted read-only mode, EXPLAIN, index advice | Slow maintenance |
| data-motherduck | 519 | Read-only default, 5 tools | MotherDuck cloud bias |
| data-supabase-pg | 2.4k | Generic Postgres performance rules | Second skill is Supabase-only |
| data-sanjay-pg | 422 | Read-only query skill | Mixed quality repo |
| ha-zigbee2mqtt | 5 | Mesh map, binding, OTA; three write tiers | 5 stars; safe tier still actuates locks |
| ha-official | core | Official, OAuth with PKCE, exposed entities only | Assist-level only; no automation editing |
| ha-skill-komal | 947 | Validate, deploy, debug automations, dashboards | Root SSH and long-lived token in examples |
| ha-hass-mcp | 343 | Dry-run on dashboard edits; tests | No auth on HTTP; includes restart |
| ha-mcp | 4.6k | 87 tools incl. automations, backups, HACS | Unofficial; broad write access |
| sap-vsp | 454 | \~200-token focused mode; read-only plus allowlists | Expert mode \~40k tokens |
| sap-adt-mario | 172 | Read-only by design | Basic auth via env vars |
| sap-adt-fr0ster | 78 | Many auth methods incl. BTP | Writes to live systems |
| safe-skillspector | 19.3k | Scans skills for injection and exfiltration; `--no-llm` mode | Default LLM is NVIDIA's; OSV.dev lookups |
| harness-hookify | marketplace | Official; turns repeated corrections into hooks | Easy to accumulate hooks |
| safe-safety-net | 1.7k | Blocks destructive git and rm, also inside `bash -c`; Windows support | `npx @latest` install |
| safe-agnix | 455 | 702 rules for AGENTS.md, SKILL.md, hooks, MCP configs | Telemetry unverified |
| harness-herdr | 43.9k | Persistent agent multiplexer across SSH hosts | Windows beta |
| safe-dippy | 243 | AST-parses bash, auto-approves only safe commands | No Windows mention |
| harness-claude-hud | 28.2k | Context and usage in the status line; no network | Cosmetic |
| harness-ccusage | 19.1k | Token and cost reports from local logs | Fetches prices unless offline |
| harness-mcp-cli | 423 | Calls MCP servers without loading them into context | Experimental |
| harness-claude-squad | 8.3k | Parallel agents in tmux and worktrees | AGPL; tmux |
| safe-container-use | 4.0k | Container plus branch per agent | Experimental; remote DOCKER\_HOST unverified |
| safe-coi | 755 | Incus containers with kernel monitoring | Needs Incus |
| harness-lean-ctx | 3.8k | Local compression and caching, no telemetry by default | Proxy in the request path |
| safe-parry-guard | 45 | Local prompt-injection scanner | Gated HuggingFace models |
| mem-agentmemory | 29.3k | Local SQLite memory across agents | Background hooks |
| build-official | 180k | Official; skill evals and benchmarking | Demonstration quality |
| build-skill-seekers | 14.9k | Turns docs, repos and PDFs into skills; local mode | Heavy optional deps |
| build-context-eng | 18k | Reference on context, memory, tool design | Prose, not tools |
| build-mcp-tunnels | marketplace | Reach a private MCP via Anthropic tunnel | Routes through Anthropic |
| arch-wshobson-es | 41k (repo) | CQRS, event store, saga, projections | Depth unverified |
| wf-pypict | 100 | Pairwise test design for config matrices | Narrow |
| wf-karpathy | 221k | Tiny, all audits pass | Generic; AGENTS.md covers it |
| wf-addyosmani | 105.9k | 25 lifecycle skills incl. ADRs | Duplicates AGENTS.md |
| wf-compound | 25.6k | Writes lessons to `docs/solutions/` | Another full loop |
| wf-ponytail | 165.3k | Minimal-change mode; audits pass | Always in context |
| wf-tdd-guard | 2.3k | Enforces TDD | No JVM; maintenance mode |
| wf-superclaude | 23.9k | Many modes and commands | Unverified token claims |
| wf-ctx-eng-kit | 1.6k | Modular, documents its own overhead | GPL; 5 to 35x tokens |
| wf-ecc | 282.1k | Huge, Windows supported | Heavy always-on rules; paid tier |
| re-wshobson | 41k (repo) | Method knowledge that complements the MCPs | protocol-RE has a Socket warning |
| re-sickn33 | 47.9k (repo) | Authorization gate before acting | Generic |
| sec-official | marketplace | Edit-time warnings plus verified-finding scans | Anthropic-only perspective |
| rev-official | marketplace | Multi-agent PR review with confidence scores | Overlaps your milestone review |
| sec-getsentry | 1.1k | skill-scanner, GHA security review | Much is Sentry-specific |
| fe-webapp-testing | 180k | Official Playwright testing of local apps | Demonstration quality |
| fe-vercel-wdg | 32.6k | 100+ accessibility and UX rules | React bias |
| fe-cf-web-perf | 2.8k | Core Web Vitals audit | Cloudflare-centric repo |
| fe-web-assets | 490 | Favicons, OG images, only Pillow | Narrow |
| fe-agent-browser | 41.1k | Rust browser CLI | Snyk medium risk |
| fe-playwright-skill | 3.0k | Simple | Installs its own Chromium |
| fe-slides | 28.6k | Single-file HTML decks | Off-profile |
| fe-design-taste | 98.4k | Art direction references | Overlaps frontend-design |
| wr-vercel-writing | 32.6k | 80+ prose rules from Vercel's handbook | Overlaps humanizer |
| rs-searxng | 1.2k | Self-hosted search, blocks private URLs, PDF reading | Needs SearXNG |
| rs-kagi | 458 | Official, 2 tools | Paid |
| wr-hand-drawn | 75 | Excalidraw diagrams for docs | Hosted editor by default |
| rs-tapestry | 560 | Article and YouTube transcript ingestion | Learning skills are fluff |
| rs-waza | 7.3k | URL or PDF to Markdown | Audits unverified |
| rs-firecrawl | 630 | Self-hostable scraping | Credits otherwise; no license shown |
| rs-nature | 48.2k | Figures, reference checks | Socket warning |
| wr-visual-docs | 666 | HTML architecture diagrams | 22 commits |
| rs-last30days | 64.5k | Multi-source recent research | Paid keys |
| ee-kicad-happy | 1.1k | Review, EMC, SPICE, BOM, fab prep for KiCad 5 to 10; 729 commits | Distributor keys for sourcing |
| ee-mcu-skills | 17 | Pin maps and HAL pitfalls per board | Small; no ESPHome |
