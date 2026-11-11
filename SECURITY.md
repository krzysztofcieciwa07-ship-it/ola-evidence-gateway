# Security Policy

## Current status

This repository currently contains a draft specification and editor configuration only. It has no executable gateway, API, storage, authentication, CI, or production deployment. It is **not a security-reviewed or production-ready service**.

## Reporting

Report suspected vulnerabilities privately through the repository's GitHub private vulnerability reporting channel when enabled. Otherwise contact the maintainer privately through GitHub. Do not include credentials, customer data, access tokens, private keys, or actionable exploits in public issues.

## Requirements before implementation or deployment

- Authenticate and authorize every evidence source and collector.
- Enforce tenant isolation at the persistence and retrieval boundary.
- Apply strict input, file-size, nesting-depth, and time limits.
- Use outbound network allowlists for remote collection.
- Protect evidence confidentiality at rest, in transit, and in exports.
- Separate content integrity from source identity, authorization, and truth claims.
- Preserve append-oriented history and explicit supersession/correction links.
- Never promote UNKNOWN to PASS.
- Keep credentials out of logs, examples, artifacts, and evidence payloads unless explicitly required and protected.

A hash chain or signed digest is not a substitute for access control, secure key management, or trustworthy collection.

## Production claims

No production claim is valid until source, tests, threat model, deployment, runtime health, retention, backup, and incident-response evidence exist for an exact release SHA.
