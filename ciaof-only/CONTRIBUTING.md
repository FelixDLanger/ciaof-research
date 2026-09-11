# Contributing

Contributions are welcome, with one standing constraint: this repository backs published research,
so changes that affect any reported number require more than a passing test.

## Before opening a pull request

- **Changes to the analysis pipeline** must state which reported results they affect, and include the
  before/after values. A change that alters a published coefficient without saying so will be closed.
- **New estimators or tests** must ship with a validation: recovery of a planted effect on synthetic
  data, and calibration under a simulated null. See the existing estimator validations for the
  standard expected.
- **New dependencies** are discouraged. If a package supplies work that is elementary to implement,
  implement it — a dependency is a replication risk. Where one is genuinely necessary, justify it.
- **Cache and I/O changes** must preserve the self-healing property: the pipeline detects and repairs
  stale state in code, and never instructs a human to delete a file or re-run a cell.

## Style

- Every analysis cell publishes its result to a named global and degrades to a printed banner when
  upstream state is missing. No cell may raise on an empty upstream state.
- Comments explain *why*, particularly where a non-obvious choice prevents a specific failure.
- Deterministic methods are preferred to probabilistic ones wherever both can answer the question.

## Reporting a problem with a published number

Open an issue with the run diagnostic block and the specific cell output. Reported numbers are
reconciled against the archived run before any correction is issued.
