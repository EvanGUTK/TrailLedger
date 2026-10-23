# TrailLedger — milestone roadmap

Milestones are ordered by dependencies, not promised calendar dates. No implementation milestone is complete in this blueprint revision.

| Milestone | Deliverable | Exit criteria |
| --- | --- | --- |
| M0 — Evidence model | Manifests and lifecycle rules | Review identity, completeness, and graph invariants |
| M1 — Local ledger | Registry and content-addressed artifact staging | Duplicate, corrupt, and partial imports handled |
| M2 — Runner slice | Synthetic experiment lifecycle | Failure, cancellation, and retry records preserved |
| M3 — Evaluation | Versioned plans and domain metric adapter | Known leakage fixture flagged with bounded claim |
| M4 — Reproduction | Portable bundle and static comparison | Clean-workspace verification works |
| M5 — Ecosystem | TapeForge and EconomyLab imports | Domain semantics preserved through shared envelope |

## Definition of done

A milestone has a bounded scope, implementation revision, synthetic reproduction input, expected output, validation evidence, and a short demonstration. Setup instructions work in a clean supported environment. Failure behavior is documented alongside the ordinary case. The project status file advances only when the exit criteria are met.

## Scope control

The first milestone cannot depend on a sibling project or hosted service. Optional integrations follow standalone correctness. Performance optimization follows a representative workload and a repeatable baseline. New UI surfaces require a demonstrated user task. Dependencies and licenses are recorded when adopted; exact versions are pinned with implementation.

## Work sequencing

Review [IMPLEMENTATION_HANDOFF.md](IMPLEMENTATION_HANDOFF.md) before creating worktrees. Keep contract changes separate from adapter changes where that allows a reviewer to understand compatibility. A change that invalidates an earlier milestone must update its acceptance evidence and status, not simply append a new roadmap item.

## Deferred expansion

No promise of universal leakage detection, automatic scientific validity, hosted multi-tenant service, model deployment platform, automatic access to proprietary data, or mandatory replacement of existing experiment tools. A plugin may import external tracking records with their original limitations preserved.

Open decisions in [DECISIONS.md](DECISIONS.md) should be resolved by a small experiment or a documented requirement. They are not a reason to build every alternative.
