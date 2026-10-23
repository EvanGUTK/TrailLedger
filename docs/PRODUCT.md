# TrailLedger — product specification

## Intended outcome

Build a local experiment and artifact ledger that connects hypotheses, dataset manifests, transformations, configurations, execution environments, results, and review decisions. Support domain-specific metrics through adapters while keeping provenance and lifecycle semantics common.

## Primary users and jobs

| User | Job | Successful outcome |
| --- | --- | --- |
| Researcher | Preserve the full experiment context | Reproduce a result or explain exactly what is missing |
| Reviewer | Evaluate a claimed improvement | Inspect trial history, benchmarks, assumptions, and amendments |
| Simulation developer | Compare configurations and seeds | Use the same evidence tooling with domain-specific metrics |

## First journey

A researcher registers a hypothesis before running a parameter search. TrailLedger fingerprints the dataset and records every trial, including failures. An attractive result is later corrected because a feature used information unavailable at decision time. The corrected experiment becomes a new lineage branch, the earlier report remains visible as superseded, and another machine verifies which inputs are available before reproducing the run.

## Functional requirements

| ID | Requirement | Acceptance evidence |
| --- | --- | --- |
| FR-01 | Hash actual inputs or declare unavailable fingerprints | Same path with different contents becomes a different dataset version |
| FR-02 | Record failed and cancelled trials | Trial counts reconcile with requested work and known interruptions |
| FR-03 | Version evaluation plans | Amendments cannot overwrite the initial registered plan |
| FR-04 | Publish complete manifests atomically | A missing required file cannot produce a successful completed status |
| FR-05 | Detect lineage cycles and incompatible schemas | Invalid import leaves the existing ledger intact |
| FR-06 | Support portable local verification | Bundle import validates hashes without the original filesystem layout |

## Scope and product constraints

Local CLI specification, one generic execution adapter, content fingerprints, a run lifecycle, chronological evaluation metadata, complete trial registration, static comparison reports, and a portable bundle using synthetic data. TapeForge and EconomyLab adapters are later milestones.

No promise of universal leakage detection, automatic scientific validity, hosted multi-tenant service, model deployment platform, automatic access to proprietary data, or mandatory replacement of existing experiment tools. A plugin may import external tracking records with their original limitations preserved.

## Product quality requirements

Every visible result identifies its source version and completeness. Repeating an action cannot silently create duplicate domain effects. Invalid input produces an actionable diagnostic tied to the field or event that failed validation. Long operations report progress and cancellation boundaries. A cancelled or interrupted operation is visibly different from a completed one.

The initial deployment is a single-user local workflow. Collaboration, tenancy, mobile apps, hosted services, billing, and distributed orchestration are separate scope decisions. An interface proposal must explain the user task it supports before adding new screens or infrastructure.

## Success and non-success

A new local workspace can verify and reproduce a small synthetic run using its bundle. Changing one input changes lineage identity. Corrupt files, cycles, incomplete runs, and missing restricted inputs are reported without a false completed or reproducible status.

Repository stars, document length, and interface polish do not substitute for the domain acceptance criteria. A result that cannot be explained or reproduced remains provisional. Scope expansion is deferred until the first complete scenario can be demonstrated and reviewed.

## Open product decisions

- Which minimal metric adapter should ship first?
- How should non-deterministic numerical reproduction be classified?
- Which external experiment tracker imports have a demonstrated user need?
