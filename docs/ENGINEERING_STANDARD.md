# Repository Engineering Standard

This repository currently holds a specification. This standard defines the controls required before it becomes an executable service.

## Source of truth

- The canonical OLA runtime source and its tests define current implemented behavior.
- This repository's documents are proposals until a contract is approved and implemented.
- Documentation does not prove runtime capability.
- Avoid duplicating evidence storage or API behavior across repositories without a documented boundary decision.

## Minimum implementation standard

1. Version schemas and validate them at every trust boundary.
2. Enforce authentication, authorization, tenant scope, and source allowlists server-side.
3. Bound payload size, nesting depth, execution time, retries, and remote egress.
4. Separate content digest, provenance, signatures, verification results, and decisions.
5. Use append-oriented records and explicit correction/supersession semantics.
6. Protect sensitive evidence with encryption, least privilege, and retention controls.
7. Add unit, integration, adversarial, tamper, and cross-tenant tests.
8. Bind CI artifacts and release attestations to the exact source commit.

## Verification vocabulary

- PASS: a named check completed successfully on the exact source SHA.
- FAIL: a check ran and failed.
- PARTIAL: only some required checks or scenarios were covered.
- BLOCKED: a required prerequisite was unavailable or failed.
- UNKNOWN: evidence is insufficient.

A skipped check is not a pass. A digest is not proof of source truth. A passing test double is not a live external-source test.

## CI and release

Do not add a workflow that always passes merely to create a green badge. Add CI when executable source and test contracts exist. Before production deployment, define backups, retention, key rotation, monitoring, rollback, and independent release evidence.
