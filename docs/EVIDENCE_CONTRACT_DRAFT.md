# Evidence Contract Draft

**Status: DRAFT / NOT AN IMPLEMENTED API**

This document proposes a minimal, versioned contract for a future OLA Evidence adapter. It must be reconciled with the actual evidence model in the canonical OLA runtime before implementation.

## Design constraints

- Separate source observations from AI interpretation and decisions.
- Preserve the exact content identity of the captured artifact.
- Preserve source, collector, timestamp, tenant, and run context.
- Make corrections additive and traceable rather than silently overwriting historical evidence.
- Keep verification outcomes distinct from record existence.
- Treat evidence as sensitive data, not as public merely because it is hashed.

## Proposed logical record

~~~json
{
  "schema_version": "0.1-draft",
  "evidence_id": "ev_example",
  "tenant_id": "tenant_example",
  "source": {
    "kind": "system",
    "identifier": "source_example"
  },
  "captured_at": "2026-11-11T12:00:00Z",
  "collector": {
    "id": "collector_example",
    "version": "0.1.0"
  },
  "content": {
    "media_type": "application/json",
    "digest": {
      "algorithm": "sha256",
      "value": "..."
    },
    "reference": "protected://artifact/example"
  },
  "links": {
    "run_id": null,
    "mission_id": null,
    "policy_ids": [],
    "decision_ids": [],
    "supersedes": null
  }
}
~~~

All names and fields above are proposals. No schema validator, serializer, or storage implementation exists in this repository today.

## Verification states

- \`PASS\`: the evidence satisfies a named, versioned verification rule.
- \`FAIL\`: the evidence exists but violates a rule.
- \`UNKNOWN\`: the available evidence is insufficient.

The verification record should identify the rule ID and version, verifier identity/version, result, reason, and the evidence digest it evaluated.

## Integrity and provenance are separate

A SHA-256 digest can detect content changes relative to a trusted recorded digest. It does not prove who submitted the evidence, whether collection was authorized, whether the source was truthful, or whether the content is confidential.

Signatures, identity, authorization, secure timestamps, and source trust require separate mechanisms and threat models.

## Open design decisions

- Canonical evidence schema and compatibility/versioning policy.
- Tenant identity and authorization source.
- Payload storage, encryption, retention, and deletion policy.
- Large-file streaming and maximum payload size.
- Source allowlists and network egress controls for remote collectors.
- Signature format and key rotation.
- Idempotency and duplicate evidence semantics.
- Correction/supersession semantics.
- Audit export format and verification tooling.

Do not resolve these decisions through undocumented implementation choices.
