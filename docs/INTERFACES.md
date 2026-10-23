# TrailLedger — interfaces and integration specification

All interfaces below are proposed contracts. Names describe responsibilities rather than installed APIs.

| Boundary | Request / input | Response / output | Guarantee |
| --- | --- | --- | --- |
| RegisterHypothesis | Question and planned evaluation | Hypothesis revision | Later amendments preserve initial registration |
| CreateRun | Effective manifest and input references | Run and attempt identity | Canonical config fingerprint and unique identity |
| AppendLifecycle | Run identity + stable event identity | New status revision | Idempotent state transition |
| PublishArtifacts | Artifact index + digests | Accepted completed manifest | Mandatory file and hash validation |
| ImportBundle | Portable bundle + rights/availability metadata | Import report and lineage references | Staged validation prevents partial accepted graph |
| ExportComparison | Selected runs + metric adapter | Static report | Incompatibilities appear before aggregate comparisons |

## Domain-specific behavior

External tools can write manifests without adopting a TrailLedger runner. Integration therefore starts with exported artifacts, not subprocess control. A runner adapter declares whether it supports checkpoints, cancellation, environment capture, and deterministic reproduction. Financial leakage checks are named rules for known patterns, never a blanket “leakage-free” certification.

## Import and export rules

Imports validate schema version, domain units, source identity, completeness, payload hash, and declared capabilities. An unsupported optional capability is surfaced to the caller; mandatory capability gaps reject the request. Exporters include contract version and a provenance manifest, and must not require direct access to an internal database.

Request identities are stable across retries. Repeated completed requests return the recorded result or an explicit duplicate result; requests with an existing identity and different content are rejected. Timeouts distinguish a known rejection from an unknown external outcome. Consumers cannot infer that an action did not happen merely because a response was lost.

## Shared conventions

Use [CONTRACTS.md](CONTRACTS.md) for envelope, time, precision, and compatibility conventions. File-based interoperability is the first integration target. Binary or local process protocols can follow after a measured need and a conformance test. A contract's ownership is recorded in [ECOSYSTEM.md](ECOSYSTEM.md).

## Consumer conformance checklist

The future adapter must demonstrate valid import, unsupported-version rejection, precision-preserving round trip, duplicate handling, corrupt-artifact rejection, and recovery from a truncated output. This checklist specifies future evidence; it does not assert that an adapter already exists.
