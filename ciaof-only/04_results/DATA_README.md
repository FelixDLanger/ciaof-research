# Data

## `archived_run_summary_FULL.txt`

The complete, unedited output of the archived analysis run (panel hash `736040245229`). It is
retained whole rather than trimmed to this paper's sections, because editing an archived artefact
defeats its purpose. It therefore contains measurement analyses that support a separate study and are
not reported in the CIAOF paper; every CIAOF figure in the paper traces to a line in this file.

## What is in this repository

Derived outputs only:

- `main_results.csv` — H1/H2 coefficients, standard errors, p-values, n
- `specification_curve.csv` — every specification in the curve
- `placebo_falsification.csv` — falsification battery results
- `ciaof_dimension_level.csv` — dimension-level estimates

## What is not, and why

**Raw filing text** is not redistributed. It is retrievable from SEC EDGAR, which is public, but the
cache runs to several gigabytes and is regenerable by running the pipeline. The pipeline caches it on
first run.

**SimFin standardized fundamentals** are licensed and are not redistributable. Obtain them directly.
The pipeline's discovery layer resolves them by column content, so file naming does not matter.

**The frozen analysis panel** (`panel_frozen.parquet`) contains licensed fundamentals and is
therefore not committed. Its hash is reported in the run summary and in the paper, so a replication
can confirm it has reconstructed identical data.

## Reproducing the panel

Run the notebook against your own SimFin extract plus the SEC data the pipeline retrieves. The
derivation layer reports every field's formula and every source's row contribution, so any divergence
from the published panel is locatable field by field.

## Provenance

Sources: SEC EDGAR full-text filings; SEC XBRL company facts; SEC submissions metadata; SimFin
standardized fundamentals. Window 2019–2025. No proprietary, internal or client data of any kind.
