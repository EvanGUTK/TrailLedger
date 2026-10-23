# TrailLedger — operations and recovery plan

## Initial operating model

Use a local metadata database and artifact root outside the repository for large runs. Maintain backup/restore of both the database and content index. Provide an orphan audit before garbage collection; referenced artifacts are never deleted because a UI filter hides their run.

## Startup protocol

Load and validate the effective configuration; record its digest. Verify schema compatibility, output permissions, free storage, and required source availability. Recover or quarantine incomplete prior work before accepting new commands. A startup failure identifies the failed prerequisite and leaves accepted artifacts untouched. Show the exact active environment and mode in diagnostics.

## Failure handling

If a runner disappears, preserve its last observed state and reconcile its terminal record before retrying. An artifact hash mismatch quarantines that artifact and invalidates dependent completeness claims. Restricted inputs remain references with acquisition instructions and rights metadata. An import with broken edges is staged for diagnosis, not partially inserted into the accepted graph.

## Persistence and backup

Configuration, immutable manifests, and accepted outputs have distinct lifecycles. Before adopting a backup as valid, restore it into a separate location and verify artifact digests and a representative result. Checkpoint frequency is a measured tradeoff between storage and recoverable work. The application never assumes a process supervisor or the browser session is a durable state store.

## Diagnostics and resource boundaries

Logs record run, input, and correlation IDs. Counters distinguish attempts, accepted work, duplicates, failures, and retries. Disk exhaustion has a defined stop condition. Large files live outside Git. Credentials and user-private artifacts are excluded from logs and public diagnostics. External-service adapters record their endpoint class, permission needs, quotas, and recovery policy when implemented.

## Release lifecycle

Build from a recorded revision, validate setup in a clean environment, run the domain acceptance scenarios, and create release notes that identify known limitations. Schema migrations require a tested reverse or restore path. A rollback preserves raw evidence and records which derived outputs require recomputation. Public issue reports should use synthetic reproductions where possible.
