# TrailLedger — data model

## Canonical entities

| Entity | Identity / fields | Lifecycle / invariant |
| --- | --- | --- |
| Hypothesis | Question, rationale, registration revision, amendments | Initial statement preserved |
| DatasetManifest | Content references, coverage, schema, rights, gaps | Missing bytes and unknown rights are explicit |
| TransformManifest | Code revision, parameters, inputs, output schema | Transform identity participates in result lineage |
| EvaluationPlan | Splits, timing, costs, benchmarks, metrics | Versioned before selected evaluation |
| Run / Attempt | Config hash, environment, seed, lifecycle, predecessor | Attempt outcomes preserved individually |
| Artifact | Digest, size, media/schema type, location hints | Location can change without changing bytes |
| ClaimReview | Claim, reviewer notes, supporting runs, supersession | A report may be withdrawn without deleting history |

## Domain semantics

A financial metric and a game metric may share storage conventions without being comparable. Return requires horizon, valuation, costs, exposure, and benchmark context; progression time requires agent policy, economy config, seed, and event rules. A non-deterministic ML run records seeds and environment but does not claim bit-identical GPU behavior unless independently demonstrated. Reproduction can be classified as byte-identical, numerically within tolerance, behaviorally equivalent, unavailable, or failed.

## Units, nulls, and identifiers

- Every metric identifies its definition, unit, sample, filters, and aggregation method.
- Source data, transformations, feature definitions, split plans, and costs participate in lineage.
- A failed or incomplete trial is not removed from the search record.
- A hash proves byte identity, not correctness, legality, or scientific validity.
- Comparable results must declare compatible evaluation and execution assumptions.

An absent value, unknown value, invalid value, and numerical zero are distinct. Identifiers preserve source namespaces. Timestamps identify clock and precision. Collections specify whether their order is semantically significant. Statistical summaries specify population, filters, denominators, and time window. Serialization decisions must survive a cross-language round trip without precision loss.

## Storage and migration

Immutable source evidence is stored separately from derived views. A migration names source and destination versions, checks prerequisites, and produces a validation report. The prior accepted artifact remains available until the replacement passes its checks. Changes to meaning or units require a new schema major version. A path rename does not alter content identity; a corrected input changes lineage even when the filename is unchanged.

## Retention and portability

Keep manifests and compact diagnostics for accepted runs. Large raw inputs may live outside Git and carry availability and redistribution metadata. An export includes a relative artifact index and integrity digests, avoiding machine-specific absolute paths. Reports clearly identify missing or restricted inputs. User-generated or private information is included only in deliberately selected export scopes.
