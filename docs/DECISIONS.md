# TrailLedger — architecture decision register

Status meanings: **proposed** is the current blueprint choice; **open** needs a bounded experiment before implementation. No choice here proves runtime behavior.

| ID | Status | Decision | Alternative / consequence |
| --- | --- | --- | --- |
| ADR-001 | Proposed | Artifacts can be registered without a managed runner | Reduces coupling to a particular research framework |
| ADR-002 | Proposed | Metadata and artifact bytes are separate | Requires coordinated backups but supports restricted datasets |
| ADR-003 | Proposed | All trials remain visible | More storage and review work; necessary for an honest search history |
| ADR-004 | Proposed | Domain metrics use adapters | Prevents a universal score from conflating unrelated experiments |

## Open questions and resolution method

- **Which minimal metric adapter should ship first?** Resolve with a minimal fixture, an explicit requirement, or a recorded compatibility check before expanding the corresponding milestone.
- **How should non-deterministic numerical reproduction be classified?** Resolve with a minimal fixture, an explicit requirement, or a recorded compatibility check before expanding the corresponding milestone.
- **Which external experiment tracker imports have a demonstrated user need?** Resolve with a minimal fixture, an explicit requirement, or a recorded compatibility check before expanding the corresponding milestone.

## Change protocol

Each new decision records context, considered alternatives, selected option, downside, acceptance evidence, and the condition that would trigger reconsideration. Superseded decisions remain in the register. A rejected alternative is recorded only when it explains a continuing tradeoff. Review decisions at milestone boundaries rather than changing foundational contracts incidentally during UI work.
