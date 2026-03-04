# Talk to the Codebase (TTC)

**Governance-grade codebase intelligence, built for AWS.**

Talk to the Codebase (TTC) helps teams analyze and understand software repositories with **evidence-based insights**, governed agents, and enterprise-ready controls.

TTC is designed for **100% AWS environments** and integrates with foundation models through **Amazon Bedrock**. Agent orchestration and catalog management can be implemented using **Bedrock Agent Core + Strands**.

---

## What you get in this repository

This repository is the **project scaffold**: documentation, contracts, configuration templates, and agent/catalog structure.

It intentionally **does not** include:
- customer code or datasets
- embeddings, indexes, exports, logs
- credentials or secrets
- internal design notes

---

## Core principles

- **Evidence first**: outputs include verifiable references (path, location/range, snapshot, run id). If evidence cannot be produced, return `insufficient_evidence`.
- **Read-only by default**: analysis runs do not mutate repos or infrastructure unless explicitly enabled by policy.
- **AWS-first**: deploy and operations assume AWS services and private networking patterns.
- **Governed agents**: skills/agents are treated as versioned artifacts with explicit scope and permissions.

---

## Repository structure

```
contracts/          TTC API + protocol contracts (OpenAPI, MCP tools, schemas)
schemas/            Canonical data schemas (evidence, run ledger, exports)
agents/             WAF agents + custom agents + catalog metadata
config/             Deployment profiles and Bedrock model/provider configuration
docs/               Additional documentation
examples/           Example repos and MCP client configuration samples
scripts/            Helper scripts for local workflows (no secrets)
var/                Local-only artifacts (gitignored)
```

---

## Model integrations (AWS)

TTC uses a **Model Gateway** abstraction. In AWS deployments the gateway calls **Amazon Bedrock** for:
- text generation / reasoning
- embeddings
- reranking (when applicable)
- agent orchestration (Agent Core + Strands)

> Note: some clients and tools use “OpenAI-style” request/response shapes. TTC may support that *shape* as an adapter, but the **runtime execution stays in AWS** and does not require OpenAI services.

See:
- `config/models/bedrock.yaml`
- `ARCHITECTURE.md`

---

## License

Apache License 2.0
