# Roadmap

This roadmap is oriented to an **AWS-first** delivery.

## Phase 0 — Scaffold (current)
- Repository structure, contracts directory, schemas, and docs
- Configuration templates for `demo/dev/prod`
- WAF agent catalog structure (placeholders only)

## Phase 1 — WAF On-ramp (P0)
Goal: `repo → snapshot → WAF run → export` with evidence.

- CLI workflow (`snapshot`, `waf run`, `export`)
- WAF agents (6 pillars) with a stable finding schema
- Run ledger and export schemas enforced
- Model Gateway integration with Amazon Bedrock

## Phase 2 — MCP Distribution (P1)
Goal: TTC usable from existing IDE/CLI surfaces via MCP.

- MCP server (read-only by default)
- Example configs for Continue/Cursor/Codex/Amazon Q/Kiro
- Agent catalog packaging and promotion workflow
- Benchmarks for latency/cost/evidence coverage

## Phase 3 — Enterprise readiness (P2)
Goal: operational hardening and extensibility without breaking governance.

- Offline-first supply chain (mirrors, private artifacts)
- Eval harness and regression gates (prompt injection, scope bypass)
- Optional agent orchestration using Bedrock Agent Core + Strands
- Release process (SemVer, changelog, security policy)
