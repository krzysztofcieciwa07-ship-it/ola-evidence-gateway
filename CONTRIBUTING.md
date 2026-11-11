# Contributing to OLA Evidence Gateway

This repository currently contains a draft specification, not an executable gateway. Contributions should improve the contract or provide a reviewed implementation plan without claiming unimplemented behavior.

## Before changing the specification

1. Read README.md, docs/EVIDENCE_CONTRACT_DRAFT.md, and docs/ENGINEERING_STANDARD.md.
2. Check whether the canonical OLA runtime already implements the proposed capability.
3. Identify tenant, provenance, retention, confidentiality, and compatibility effects.
4. Keep changes focused and label draft decisions explicitly.

## Implementation work

Do not add a second persistence or API implementation until the canonical ownership boundary and contract are agreed. When executable source is introduced, add deterministic tests, CI, local setup, and deployment/rollback instructions in the same implementation series.

## Pull requests

- State whether the change is specification-only or executable.
- Identify the exact source commit and tests actually run.
- Do not claim PASS, production readiness, or independent verification without evidence.
- Document unresolved decisions rather than hiding them.
