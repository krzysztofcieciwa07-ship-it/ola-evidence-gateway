# OLA Evidence Gateway — implementation status

**Snapshot:** 2026-11-18  
**Repository status:** `SPECIFICATION ONLY / NOT IMPLEMENTED / NOT RUNTIME-VERIFIED`

## Verified repository boundary

The default branch contains documentation, repository governance, and editor/development-container configuration. It does **not** contain:

- an executable Evidence Gateway server or API entry point;
- a persistence implementation or deployable database schema;
- a runnable test suite for a gateway service;
- a build/package manifest for a gateway application;
- a container image definition or deployment workflow for a gateway service;
- runtime health checks or production deployment evidence.

The README and documents describe a proposed architecture and contract. They are not evidence that the described API, hashing, signing, storage, independent verification, replay protection, or export features exist in this repository.

## Current evidence classification

| Capability | Status | Evidence boundary |
|---|---|---|
| Architecture and purpose | DOCUMENTED | README and draft contract |
| Versioned evidence schema | PROPOSED | Draft only; no schema validator |
| API/server | NOT IMPLEMENTED | No executable server source |
| Persistence | NOT IMPLEMENTED | No gateway database implementation |
| Cryptographic signing | NOT IMPLEMENTED HERE | Requirements only |
| Independent verification | NOT IMPLEMENTED HERE | Requirements only |
| Tamper/replay tests | NOT IMPLEMENTED HERE | No gateway test suite |
| Tenant authorization | NOT IMPLEMENTED HERE | Requirements only |
| CI for gateway runtime | NOT CONFIGURED | No executable gateway workflow |
| Production deployment | UNKNOWN / NOT EVIDENCED | No deployment artifact or health proof |

## Canonical ownership

The canonical OLA runtime repository is:

https://github.com/krzysztofcieciwa07-ship-it/OLA

That repository contains its own evidence-related implementation and must be assessed independently at an exact commit SHA. Its code does not make this specification repository a running gateway.

Do not create a second evidence store, API, or authorization plane here without an explicit architecture decision defining ownership, contracts, migration, and operational responsibility.

## Minimum implementation gate

Before this repository can be described as an executable service:

1. Approve a versioned contract and threat model.
2. Define tenant identity, authorization, source allowlists, retention, encryption, and deletion.
3. Implement one vertical slice: authorized input → canonicalization → digest → append-only persistence → independent verification → export.
4. Add schema, unit, integration, cross-tenant, tamper, replay, and mutation tests.
5. Add bounded payload size, nesting depth, execution time, retries, and outbound network destinations.
6. Add reproducible local setup, CI, container/build artifacts, deployment, health checks, and rollback.
7. Bind release evidence to exact source SHA and deployed artifact digest.

## Decision

**Keep this repository specification-only.** Do not connect production customer data, secrets, deployment targets, or release claims to it until the implementation gate is met.

A hash proves byte equality against a trusted digest. It does not prove source truth, identity, authorization, or confidentiality.
