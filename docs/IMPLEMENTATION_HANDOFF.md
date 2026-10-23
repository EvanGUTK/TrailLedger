# TrailLedger — implementation handoff

## Read order

Read PRODUCT, DATA_MODEL, PIPELINE, and VALIDATION before selecting a work package. This repository currently contains documentation and original identity artwork only. Do not infer an executable stack from proposed folder names.

## Proposed module hierarchy

| Planned path | Responsibility | Dependency boundary |
| --- | --- | --- |
| ledger/ | Manifest validation, lineage, lifecycle, artifact index | No domain metric assumptions |
| adapters/ | Runner and domain import/export | Capability declarations required |
| reports/ | Static evidence rendering | Reads accepted manifests |
| cli/ | Local experiment operations | Calls application boundary |
| contracts/ | Manifest and comparison schemas | Versioned ownership |
| fixtures/ | Synthetic experiments and broken bundles | No restricted inputs |

## First work packages

| Package | Deliverable | Acceptance / review |
| --- | --- | --- |
| WP-01 | Canonical manifest hashing and graph rules | Changed-content and cycle fixtures |
| WP-02 | Transactional run lifecycle | Unknown worker outcome and idempotent retry |
| WP-03 | Atomic artifact publication | Truncated and corrupted bundle cases |
| WP-04 | Synthetic reproduction report | Clean-workspace verification |
| WP-05 | One domain adapter | Metric compatibility and provenance round trip |

## Engineering discipline

Each work package should fit one reviewable behavior. Define the fixture and expected output before broadening the interface. Keep domain code independent of the UI and external adapters. Add meaningful tests for state transitions, failure recovery, and numerical semantics; avoid tests that simply restate an implementation. When a contract changes, update its fixture and every affected importer together or preserve a compatibility layer.

Use a short-lived feature branch from main. A worktree is optional and should correspond to a bounded task; no permanent development branch is required. Commit the smallest coherent change with its documentation and validation evidence. Merge only after the package's acceptance criteria are met. Do not add empty frameworks, unverified installation commands, dummy benchmark results, or success badges.

## First reviewer checklist

The reviewer can explain where canonical state lives, what event order means, which values carry units, how a retry is recognized, and how a partial result is rejected. The reviewer can reproduce the smallest scenario without credentials or another project. A larger implementation plan should be revised from the observed first slice rather than treating every proposed directory as a requirement.
