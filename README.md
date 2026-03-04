# Talk to the Codebase (TTC)

**Governance-grade codebase intelligence.**

TTC helps teams **understand, audit, and improve software repositories** using evidence-based insights, governed agents, and enterprise-ready architecture.

Instead of acting as a generic chat assistant, TTC analyzes repositories and produces **traceable insights backed by code evidence** — making results auditable, reviewable, and reproducible.

---

# ✨ Why TTC

Modern code assistants optimize for **speed of generation**.

TTC optimizes for **confidence and governance**.

Key principles:

* **Evidence-first answers**
  Every insight references real files, paths, and code ranges.

* **Offline-first architecture**
  Runs inside private networks and enterprise environments.

* **Governed AI agents**
  Skills and powers are versioned, auditable, and revocable.

* **MCP native distribution**
  TTC integrates with IDE and CLI tools instead of competing with them.

---

# 🚀 What TTC Does

TTC analyzes your repository and produces insights such as:

* architecture maps
* dependency analysis
* reliability risks
* security findings
* modernization opportunities
* technical debt hotspots

All results include **evidence references** and can be exported as structured reports.

---

# 🧠 Core Concepts

## Evidence Contract

TTC responses are never free-form guesses.

Every result must include:

* file path
* code location
* snapshot reference
* reproducible run id

If evidence cannot be produced, TTC returns:

```
insufficient_evidence
```

---

## WAF Agents

TTC includes **Well-Architected Framework (WAF) Agents** that analyze repositories across six pillars:

* Operational Excellence
* Security
* Reliability
* Performance Efficiency
* Cost Optimization
* Sustainability

Each finding includes:

* severity
* impact
* recommendation
* evidence references
* estimated effort

---

## Run Ledger

Every analysis run produces a unique **run_id**.

This enables:

* reproducibility
* auditing
* exports
* traceability

---

# 🧩 Architecture Overview

High-level architecture:

```
Repository
   │
   ▼
Snapshot Engine
   │
   ▼
Indexing & Retrieval
   │
   ▼
ContextPack Builder
   │
   ▼
Governed Agents / WAF
   │
   ▼
Run Ledger + Evidence
   │
   ▼
Exports / MCP Clients
```

Key architectural properties:

* **multi-tenant isolation**
* **evidence-based RAG**
* **derived indexes rebuildable from source**
* **offline-first deployment**

---

# 🔌 MCP Integration

TTC is designed to work with **Model Context Protocol (MCP)** clients.

Supported integrations include:

* Continue
* Cursor
* Codex
* Amazon Q CLI
* Kiro CLI

TTC runs as an **MCP server**, exposing tools such as:

```
snapshot
query
run
export
status
```

This allows developers to interact with TTC directly from their IDE or CLI.

---

# ⚡ Quickstart (Planned)

```bash
git clone https://github.com/<org>/talk-to-codebase
cd talk-to-codebase
docker compose up
```

Run your first analysis:

```bash
ttc snapshot
ttc waf run --all
ttc export
```

You will receive a **WAF report with evidence references**.

---

# 📦 Repository Structure (Planned)

```
talk-to-codebase/

core/
snapshot/
retrieval/
contextpack/
agents/
waf/
mcp-server/

runtime/
control-plane/
data-plane/

docs/
examples/
```

---

# 🔒 Security Principles

TTC is designed with **enterprise security requirements**:

* Zero-Trust architecture
* Scope-based isolation
* Read-only default agents
* Offline-first deployment
* Policy-driven governance

---

# 🌍 Open Source Strategy

TTC is released as open source to enable:

* community-built agents
* extensible skill catalogs
* integrations with developer tools
* reproducible research

The open source core focuses on:

* TTC Kernel
* WAF Agents
* MCP server
* CLI tooling

---

# 🤝 Contributing

We welcome contributions from the community.

Typical contributions include:

* new analysis agents
* WAF improvements
* IDE integrations
* bug fixes and performance improvements

Please see:

```
CONTRIBUTING.md
```

---

# 📄 License

Apache License 2.0

---

# 🔭 Roadmap

Short-term roadmap:

**Phase 1**

* WAF Agents
* CLI interface
* MCP server

**Phase 2**

* Agent Factory
* multi-repo analysis
* IDE integrations

**Phase 3**

* community agent catalog
* advanced architecture analysis
* automated modernization insights

---

# 🧑‍💻 Maintainers

Talk to the Codebase is maintained by the TTC core team and community contributors.

---

# ⭐ If you find TTC useful

Please consider giving the project a star.
