# CIAOF — Core Integrity Adherence–Outcome Framework

Replication materials for the working paper *Core Integrity as a Firm Characteristic: Allocation,
Level, and the Limits of Public-Data Inference on Architectural Discipline*, together with the
decision framework the paper delivers.

**Author:** Felix D. Langer · Doctoral Candidate (DBA), GlobalNxt University · Independent Researcher
ORCID [0009-0000-3205-8088](https://orcid.org/0009-0000-3205-8088)
**Repository:** https://github.com/FelixDLanger/ciaof-research

---

## The paper in one paragraph

Enterprise-platform doctrine holds that firms should keep the standard digital core unmodified and
relocate customization to governed extensions. This paper formalizes that doctrine as a falsifiable
framework and tests it on 950 firm-years of large US filers. Adherence turns out to be overwhelmingly
a *firm characteristic* — 94% of its variance is between firms — and its level does not reliably
predict performance. The inverted-U is rejected. Selective allocation across dimensions does not
outperform uniform allocation. No dimension operates as a floor, a ceiling, or a prerequisite. A
Shapley decomposition shows the five-dimension composite is effectively two dimensions. The
conclusion is not that discipline fails to pay, but that **no universal rule is identifiable** — from
which a decision framework follows rather than a benchmark.

## The deliverable

`05_figures/ciaof_matrix.png` (Figure 1 in the paper) is the framework. Panel A classifies each
business capability on **business impact** and **standard-fit** — how completely the standard product
covers it as delivered, which is *not* how standardised the process currently is. Panel B is the
operating frame: five rules derived from the results, each carrying its warrant.

The framework is warranted by the absence of an identifiable universal rule, not by evidence that any
rule works, and it says so on its face.

## Folder map

| Folder | Contents |
|---|---|
| `02_pipeline/` | `CIAOF_pipeline.ipynb` — the analysis, one file, run top to bottom |
| `03_protocol/` | The standing research protocol and replication notes |
| `04_results/` | Archived run output and data documentation |
| `05_figures/` | The framework figure at publication resolution |

## What the evidence supports, and what it does not

| Claim | Status |
|---|---|
| Adherence is a firm characteristic (94% between-firm) | Supported — variance decomposition |
| The composite is effectively two-dimensional (88% in two) | Supported — Shapley decomposition |
| No inverted-U | Supported as a rejection (convex, p = 0.364) |
| No floor, no ceiling, no prerequisite dimension | Supported as nulls |
| No reliable association between adherence level and performance | Supported — sign unstable across 36 specifications |
| Adherence is *negatively* associated with performance | **Not supported** — p = 0.099, sign unstable |
| High adherence destroys value | **Not supported** — 0 of 4 quintile contrasts survive adjustment |
| The matrix's quadrant logic | **Not validated** — predicted sign, p = 0.107 |
| A minimum floor across dimensions | **Refuted** — minimum-dimension p = 0.529 |

## Design commitments

- **Reliability before hypotheses.** Measurement diagnostics gate what follows.
- **Deterministic before probabilistic.** A deterministic bound is preferred where one settles the
  question — exactly reproducible, no version drift.
- **Own the estimator.** Two-way fixed effects is implemented directly and validated against
  least-squares-dummy-variable estimation to machine precision. A dependency doing elementary work is
  a replication risk.
- **Declared hierarchy.** Primary, secondary and exploratory tiers fixed before estimation and
  printed with the results.
- **Falsification on every result**, including the paper's own preferred findings.
- **Self-healing pipeline.** Stale caches are detected and repaired in code, schema included.

## Reproducing

Requirements in `requirements.txt`; all are preinstalled in Google Colab. No estimator package is
required.

1. Place the source panel on Drive (or adjust `DRIVE_ROOT` in cell 0).
2. Set a SEC contact identity — Colab secret `SEC_EMAIL` or `SEC_CONTACT_EMAIL`, or answer the prompt.
3. Runtime → Run all.

The run ends with a diagnostic ladder, a CIAOF summary, and a `PAPER_NUMBERS.md` export written to
Drive — the authoritative source for every figure in the paper. See `03_protocol/REPLICATION.md`.

**Reference run:** notebook `CIAOF-1.0` · panel hash `736040245229` · seed 42 · 950 firm-years ·
167 firms · 2019–2025.

## The paper itself

The working paper is published on SSRN rather than committed here, so that one version is
authoritative and citable. This repository holds what the paper cannot: the analysis pipeline, the
protocol it follows, the archived run its numbers trace to, and the framework figure at publication
resolution.

## A note on residual identifiers in the pipeline

The analysis cells are lifted **verbatim** from the larger pipeline, and that guarantee is what makes
a result impossible to differ between branches. It has one visible consequence: cache directory
names, output filenames, the source-folder hint, the column-matching patterns and a small number of
guarded code blocks still carry historical identifiers — the name of the second research arm, and the
original project name under which the source data was assembled. Those blocks cannot execute here — the index they depend on is not built
in this branch — and the names are load-bearing: renaming the cache directories would orphan an
existing local cache and force a full re-download from SEC EDGAR.

They were therefore left alone deliberately. Column-matching patterns in particular must match the
actual column names in the source data; changing them would break discovery silently. Only
user-visible labels and comments were changed. If you would
rather have cosmetically clean identifiers than byte-identical shared code, that is a defensible
preference, but it trades away the guarantee above.

`04_results/archived_run_summary_FULL.txt` is likewise unedited, for the reason given in
`04_results/DATA_README.md`.

## Relation to the full research programme

This repository is the CIAOF branch. Every analysis cell is lifted verbatim from a larger pipeline
that also supports a separate measurement study on enterprise-architecture governance, in preparation
for release in late 2026. Nothing here is rewritten, so a result cannot differ between branches; the
measurement analyses are simply absent, and no CIAOF result depends on them.

## Licence

Code and documentation: **AGPL-3.0-or-later**. Commercial licensing available — see `COMMERCIAL.md`.
Add the licence text before publishing: `curl -o LICENSE https://www.gnu.org/licenses/agpl-3.0.txt`

## Disclosure

The author is employed by SAP. The views expressed are the author's own and do not represent the
views or positions of SAP. This research uses exclusively public data — SEC EDGAR/XBRL, filing
metadata, and SimFin standardized fundamentals — and no proprietary information, internal tooling, or
client data. The framework is vendor-agnostic by construction; the term *core integrity* is used
throughout in preference to any vendor's vocabulary.
