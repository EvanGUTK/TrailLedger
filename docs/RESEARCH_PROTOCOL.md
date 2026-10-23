# Research and evaluation protocol

## Before evaluating

Write the hypothesis, expected mechanism, target population, decision timing, benchmark, and rejection conditions. Distinguish a preregistered evaluation from exploration. Both are useful, but they make different evidentiary claims. Record how many variants are planned and preserve the actual search history.

## Financial experiments

Split chronologically. Fit preprocessing, feature selection, and model parameters using permitted training information only. Preserve an availability timestamp for features that arrive after the underlying event. Where target horizons overlap split boundaries, explicitly remove or isolate overlapping information according to the evaluation design. This is a documented domain decision, not a universal fixed embargo interval.

Execution timing, fees, spread treatment, slippage, market impact assumptions, benchmark exposure, and missing-data behavior must be declared. Report gross and cost-adjusted outcomes separately. A short convenient interval cannot establish durable alpha, and many dependent trades do not automatically create many independent observations.

## Simulation experiments

Record agent policy, environment version, economy or scenario configuration, seeds, stopping rules, and censoring. Report the distribution across independent runs. Time-to-unlock statistics distinguish players who reached a milestone from those who never reached it during the observation window. Model fit to player behavior is an empirical question outside metadata correctness.

## After evaluating

Preserve failed attempts and amendments. Explain metric selection and sensitivity. Mark a result superseded if corrected inputs or assumptions invalidate the earlier claim. Export enough evidence for a reviewer to reconstruct both the computation and the limits of its interpretation.
