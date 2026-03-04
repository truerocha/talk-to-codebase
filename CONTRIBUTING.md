# Contributing

Thanks for contributing to Talk to the Codebase (TTC).

## What belongs in this repository

This repository contains:
- contracts (OpenAPI, MCP tools, schemas)
- documentation
- configuration templates (AWS/Bedrock)
- agent catalog structure (WAF + custom)

It must not contain:
- secrets, tokens, credentials
- customer repositories or proprietary code
- embeddings, indexes, exports, logs
- large binaries

## Workflow

1. Fork the repository
2. Create a feature branch
3. Make changes
4. Run checks (when available)
5. Open a pull request

## Pull request requirements

- Keep language clear and direct.
- Update docs when changing contracts or structure.
- Maintain AWS-first assumptions in the reference config and docs.
