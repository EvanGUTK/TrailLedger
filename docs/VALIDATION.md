# TrailLedger — validation and benchmark plan

This is a proposed validation plan. No runtime results or benchmark numbers are claimed.

## Domain scenario matrix

| Scenario | Expected behavior | Evidence |
| --- | --- | --- |
| Changed bytes, same path | New dataset fingerprint | Before/after manifest comparison |
| Corrupt artifact | Integrity failure and dependent claim invalidation | Digest report |
| Worker disappears | Run remains interrupted or unknown | Lifecycle event history |
| Retry after timeout | New attempt linked without duplicate completed run | Identity and state audit |
| Cyclic lineage | Import rejected | Minimal graph counterexample |
| Missing licensed data | Metadata inspectable; reproduction unavailable | Bundle availability report |
| Different metric definitions | Comparison flagged incompatible | Metric definition diff |

## Measurement protocol

Measure registration latency, import verification by artifact count and size, lineage traversal on representative graphs, report generation time, and metadata/storage overhead. Reproduction checks use exact comparison for discrete state and declared tolerances for numerical results. Do not infer strategy validity from a successfully reproduced computation.

## Reproducibility record

Record source revision, environment and dependency lock, operating system, CPU/GPU where relevant, workload identity, input size, data distribution, random seeds, concurrency, warm-up policy, repetitions, and output digests. Report variability and failures as well as the preferred statistic. Distinguish pure kernel timing from parsing, serialization, storage, network, and UI costs. Comparisons use the same semantics and workload.

## Correctness before speed

A new local workspace can verify and reproduce a small synthetic run using its bundle. Changing one input changes lineage identity. Corrupt files, cycles, incomplete runs, and missing restricted inputs are reported without a false completed or reproducible status.

Use a small independent reference or analytically solved fixture where feasible. A second implementation that copies the same assumptions is not independent evidence of realism. Numerical comparisons define tolerances; discrete identifiers, units, and state transitions require exact agreement. Every discovered defect becomes a minimized regression scenario with its original cause explained.

## Publication rules

Illustrative values must be labeled. A benchmark badge is added only when its method and source artifacts are available. Missing data, incomplete runs, rejected inputs, and failed experiments remain in the evaluation record. No annualized financial performance, behavioral realism, or platform fidelity is inferred from a short convenient sample.
