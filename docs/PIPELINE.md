# TrailLedger — pipeline specification

## Stage contracts

| Stage | Input | Output / postcondition | Failure and recovery |
| --- | --- | --- | --- |
| Register question | Hypothesis + planned benchmark and evaluation | Immutable initial hypothesis revision | Later changes become amendments with time and reason |
| Fingerprint inputs | Dataset and transformation references | DatasetManifest and dependency graph | Unavailable or restricted bytes are explicit, never silently downloaded |
| Validate evaluation | Split plan + timing assumptions + metric definitions | EvaluationPlan with declared checks | Flag supported leakage patterns; human review remains required |
| Create run | Effective config + revision + environment | Run identity and initial manifest | Reject identity reuse with different effective input |
| Observe execution | Adapter lifecycle events | Append-only run status and trial records | A crashed worker becomes interrupted or unknown until reconciled |
| Publish artifacts | Staged files + metric definitions | Hashed accepted outputs and completed manifest | Missing mandatory artifacts prevent completed status |
| Review and reproduce | Selected run and available input references | Comparison, ancestry, and reproduction report | Missing data prevents reproducibility claim but preserves inspectable metadata |

## Ordering and checkpoints

Registry events have monotonic local revisions. Domain time belongs to the runner and is preserved separately. A completed run references a frozen effective manifest; amendments create a new run or explicitly revised claim. Checkpoints preserve adapter state where the runner supports it, but TrailLedger cannot manufacture resumability for a runner that lacks it. A retry receives a distinct attempt identity and links to its predecessor.

## Invariants across stages

- Every metric identifies its definition, unit, sample, filters, and aggregation method.
- Source data, transformations, feature definitions, split plans, and costs participate in lineage.
- A failed or incomplete trial is not removed from the search record.
- A hash proves byte identity, not correctness, legality, or scientific validity.
- Comparable results must declare compatible evaluation and execution assumptions.

## Completion protocol

An operation starts by assigning a run identity and fingerprinting its effective configuration. Input validation completes before irreversible domain effects. Intermediate files remain staged and include an incomplete marker. Completed outputs are hashed and referenced by a manifest committed atomically with their accepted status. A crash before publication leaves recoverable intermediate work, not a plausible final report.

Retries identify the prior operation and preserve the original input references. A repair that changes semantics becomes a new revision with an explicit reason. Cancellation is honored at documented boundaries and records the last committed checkpoint. Importers reject incomplete outputs by default; diagnostic tools can inspect them only with an explicit incomplete status.

## Worked scenario

Illustrative financial example: plan P1 declares training, validation, and held-out test intervals. Run R1 records a feature transform whose timestamp uses a later value. Review marks R1 unsuitable for the claimed evaluation, retains its original artifacts, and creates corrected transform T2 and run R2. The comparison identifies the changed transform and any revised timing assumptions before displaying a metric difference.

## Pipeline acceptance gate

The first vertical slice must demonstrate one ordinary case, one malformed input, one duplicate, and one interruption or recovery case. Its output includes input lineage and enough diagnostics to explain failure without reconstructing the operator's shell history. Domain-specific scenarios in [VALIDATION.md](VALIDATION.md) take precedence over generic throughput goals.
