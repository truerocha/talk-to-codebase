# Security

This document describes security expectations for Talk to the Codebase (TTC).

## Non-negotiables

- **Evidence-first**: no unverifiable answers. Outputs must include evidence references or return `insufficient_evidence`.
- **Read-only by default**: no automatic code execution or repo mutation unless explicitly enabled by policy.
- **Scope enforcement**: every request and retrieval operation must be constrained by tenant/repo/snapshot (and optional branch/path).
- **Least privilege**: service identities must use AWS-native identity (IRSA / Pod Identity) with minimal permissions.

## AWS deployment assumptions

A production profile assumes:
- private networking (VPC-only where required)
- AWS service endpoints (S3, DynamoDB, STS, Bedrock) via VPC endpoints / PrivateLink
- restricted egress (no public internet dependency for runtime)

## Data handling

- **No secrets in git**: credentials, tokens, and keys must never be committed.
- **Local artifacts are excluded**: snapshots, embeddings, indexes, exports, and logs must stay outside version control (`var/` is gitignored).
- **Minimize logs**: do not log code payloads or prompts; log only references, hashes, ids, and metrics.

## Vulnerability reporting

If you discover a security issue:
1. Do not open a public issue with exploit details.
2. Contact the maintainers privately using the process in this repository's `SECURITY.md` (this file).
