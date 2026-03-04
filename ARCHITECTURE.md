# Architecture

This document describes the **AWS-first** target architecture for Talk to the Codebase (TTC).

## Scope

TTC is a platform for repository analysis that produces **auditable outputs** backed by evidence. The platform is designed for **private networking** and enterprise operation.

This repository provides:
- contracts (API / MCP tools / schemas)
- agent catalog structure (WAF + custom)
- configuration templates (profiles, Bedrock)
- documentation

## High-level flow

1. **Repo intake** (read-only): clone/fetch and create a sanitized snapshot.
2. **Indexing**: build derived indexes (vector/lexical) from the snapshot.
3. **Retrieval**: assemble candidate evidence under strict scope filters.
4. **ContextPack**: create a context package with evidence references.
5. **Agents**: run governed analysis agents (WAF and custom).
6. **Run ledger**: record run metadata and evidence references by `run_id`.
7. **Exports**: produce Markdown/JSON artifacts tied to `run_id`.

## Core components

### Snapshot Engine
- Produces a deterministic snapshot of a repository state.
- Enforces quarantine/sandbox rules for ingestion artifacts.

### Retrieval Plane
- Supports hybrid retrieval (lexical + vector) with mandatory scope filters.
- Produces evidence candidates with stable identifiers.

### ContextPack Builder
- Builds bounded context packages for model calls.
- Enforces size limits and policy constraints.

### Agent Runtime
- Executes WAF agents and custom agents.
- Requires every finding to include evidence references.

### Run Ledger & Exports
- Each run emits a `run_id`.
- Exports are versioned artifacts linked to the run ledger.

## AWS runtime placement

A typical AWS deployment uses:

- **EKS** for TTC services and stateful components (e.g., vector DB)
- **S3** for snapshots, evidence packs, and exports (SoR)
- **DynamoDB** for catalogs and run ledger metadata
- **Step Functions** for orchestrating ingestion and long-running workflows
- **Amazon Bedrock** for model inference (text + embeddings) and optional agent orchestration
- **CloudFront + S3** for static UI delivery (optional)
- **API Gateway / ALB** for edge routing (depending on profile)

## Model Gateway (AWS)

The Model Gateway is the single integration surface for model calls.

In AWS deployments it calls **Amazon Bedrock**. If the organization uses multiple model families, the gateway selects by policy:
- `reasoning` model
- `fast` model
- `embedding` model

Agent orchestration can be implemented using **Bedrock Agent Core + Strands**, with TTC owning:
- scope enforcement
- evidence contract enforcement
- run ledger and exports

## Contracts

Contracts define how TTC components integrate:
- **BFF / API**: OpenAPI in `contracts/openapi/`
- **MCP tools**: tool contracts in `contracts/mcp/`
- **Data schemas**: `schemas/` and `contracts/schemas/`

Contracts are vendor-neutral **by design**, but the reference deployment is **AWS-only**.

## Profiles

TTC uses `demo`, `dev`, and `prod` profiles with increasing controls:
- `demo`: fast local start, single-tenant assumptions
- `dev`: enforced scoping, rate limits, audit completeness
- `prod`: offline-first, VPC-only, strict data perimeter, least privilege

See `config/profiles/`.
