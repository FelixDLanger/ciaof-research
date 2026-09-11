# Replication notes

## Determinism

The pipeline is deterministic given a fixed seed and a fixed input panel:

- All random procedures (bootstrap, randomization inference, stratified sampling) draw from a seeded
  generator declared in cell 0.
- The two-way fixed-effects and Callaway–Sant'Anna estimators are implemented in-repository; no
  external estimator package participates in any reported result.
- Optional LLM classification writes labels to disk keyed by a hash of the classified text. Those
  labels ship as data. Reruns read the file rather than re-querying, so results are identical whether
  or not the API is reachable, and unaffected by model version changes.
- The analysis panel is frozen and hashed. The hash is printed in the run summary and reported in
  the paper.

## What to check first when replicating

1. **Panel hash** — if it differs, the panels differ; do not compare coefficients until it matches.
2. **Fiscal-year reconciliation** — the run reports how many firms required the prior-year convention.
   A mismatch here silently pairs a firm's financials with the wrong year's narrative.
3. **Control coverage screen** — controls below 70% coverage are dropped automatically and reported.
   A different source panel can change the control set and therefore the estimation sample.
4. **Estimation n** — reported per outcome. Coverage and estimation n differ after complete-case
   requirements; both are printed.

## Estimator validation

- Two-way fixed effects reproduces least-squares-dummy-variable point estimates to machine precision
  on an unbalanced synthetic panel, and its clustered confidence intervals achieve nominal coverage
  in simulation.
- The Callaway–Sant'Anna implementation is calibrated under a simulated null (mean ATT ≈ 0, rejection
  near nominal) and recovers a planted staggered effect with pre-periods indistinguishable from zero.
  An optional cross-check against an external package is cached and reported when available.

## Known sensitivities

- **Sub-1% treated shares.** Event-based results with a treated share below 1% are suppressed
  automatically; they rest on too few observations to interpret.
- **Order-statistic collinearity.** Mean, minimum and maximum of the same dimensions are strongly
  intercorrelated; only single-regressor specifications are interpreted.
- **Right-skewed support.** No claim is made about behaviour at the top of the adherence range.
