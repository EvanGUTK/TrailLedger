# TrailLedger — primary source register

Prepared 2026-10-23. References inform the proposal; upstream capabilities, entitlements, quotas, and versions must be rechecked when implementing an adapter. External documentation is not proof that this repository implements an integration.

| Primary reference | Design relevance |
| --- | --- |
| [DuckDB Parquet documentation](https://duckdb.org/docs/stable/data/parquet/overview) | Candidate columnar inspection layer |
| [SQLite transactions](https://www.sqlite.org/lang_transaction.html) | Atomic metadata state and publication boundaries |
| [PyTorch reproducibility](https://docs.pytorch.org/docs/stable/notes/randomness.html) | Limits and controls for deterministic numerical experiments |

## Implementation verification tasks

Verify SQLite journal and backup choices on the supported OS. Confirm canonical serialization and hashing against cross-language fixtures. Validate each runner’s actual seed and determinism controls; recording a seed alone is insufficient.

## Evidence classification

Protocol or platform facts come from the linked primary documentation. Architecture, scope, component names, interface designs, and milestones are original proposals for this project. Future empirical claims must link their own input manifests and measurements. Do not copy provider examples, redistributable-looking data, or game art into the repository without checking the applicable license and attribution requirements.
