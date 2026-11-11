# OLA Evidence Gateway

**Repository status: SPECIFICATION / NOT IMPLEMENTED HERE**

This repository currently contains a design document and editor configuration. It does not contain an executable Evidence Gateway, API implementation, persistence layer, test suite, CI workflow, or deployment definition.

The active OLA runtime and its implemented evidence mechanisms are maintained in the [canonical OLA repository](https://github.com/krzysztofcieciwa07-ship-it/OLA). Do not infer that every capability in this specification is already implemented there or in this repository. Verify each capability against the source and tests.

## Purpose

This repository is the design boundary for a future evidence-ingestion and provenance adapter. Its proposed responsibility is to normalize observations from authorized sources and make their origin, content digest, collection context, and verification status inspectable.

The governing separation is:

~~~text
SOURCE OBSERVATION
       |
       v
EVIDENCE RECORD
       |
       v
INDEPENDENT VERIFICATION
       |
       v
DECISION / REPORT
~~~

A model interpretation is not an evidence record. A hash proves that bytes match a digest, not that the source was truthful or authorized.

## Current contents

- \`README.md\` — initial concept and design notes.
- \`.devcontainer/\` — editor container configuration.
- \`.vscode/\` — local editor launch configuration.

There is currently no runnable command. The Dev Container image alone does not make the proposed gateway executable.

## Proposed scope

The specification may cover:

- authorized evidence collection;
- deterministic content normalization where appropriate;
- cryptographic content digests;
- source and collector provenance;
- timestamps and tenant scope;
- links to runs, policies, decisions, and reports;
- integrity verification and export of audit records.

Storage, API routes, signatures, and schemas remain proposals until they are defined, implemented, and tested. Do not create a second evidence store or API that duplicates the canonical OLA runtime without an explicit architecture decision.

## Proposed evidence distinctions

| Concept | Meaning |
|---|---|
| Observation | Data captured from a source. |
| Evidence | A preserved observation plus content and provenance metadata. |
| Integrity check | Verification that content still matches its recorded digest. |
| Verification result | A rule-bound conclusion such as PASS, FAIL, or UNKNOWN. |
| Decision | An action or outcome that references its evidence and verification basis. |

\`UNKNOWN\` must never be silently promoted to \`PASS\`. Hashing alone does not prove authorship, authorization, truthfulness, or confidentiality.

## Before implementation

1. Confirm the ownership and source-of-truth boundary with the canonical OLA runtime.
2. Approve a versioned evidence schema and API contract.
3. Define tenant isolation, authorization, retention, and sensitive-data handling.
4. Implement source adapters and persistence only after the contract is accepted.
5. Add deterministic unit, integration, mutation, and cross-tenant tests.
6. Add CI and deployment workflows only when there is executable code to verify.
7. Bind release evidence to the exact source commit and deployed artifact.

## Local development

There is no install or run command at this stage. Do not publish this repository as a working gateway or connect production data to it until implementation, tests, security controls, and deployment evidence exist.

## Engineering and security

Read [docs/EVIDENCE_CONTRACT_DRAFT.md](docs/EVIDENCE_CONTRACT_DRAFT.md), [docs/ENGINEERING_STANDARD.md](docs/ENGINEERING_STANDARD.md), [CONTRIBUTING.md](CONTRIBUTING.md), and [SECURITY.md](SECURITY.md) before proposing implementation work.

No LICENSE file is present. GitHub visibility does not grant rights to reuse or redistribute the material.
