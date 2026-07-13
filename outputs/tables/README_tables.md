# Tables

This folder contains public, derived result tables for the RMCT validation and benchmarking workflow.

## Table index

| File | Description |
|---|---|
| `Section6_population_coverage_benchmark.xlsx` | Population coverage benchmark across RMCT and comparator systems |
| `Section6_capability_specificity_benchmark.xlsx` | Capability specificity benchmark comparing descriptor richness and structured capability fields |
| `Section6_Q1_Q10_balanced_dimension_baseline_results.xlsx` | Procurement-brief search benchmark comparing SIC, keyword-only, single-dimension RMCT and multi-dimensional RMCT filtering |

## Data-sharing note

These files contain aggregate or derived results. They do not include full raw website text. Where firm-level detail is needed, use anonymised company identifiers and the public data files in `data/`.

## Relationship to code

The benchmark logic is documented in:

- `code/05_benchmark_retrieval.py`
- `notebooks/rmct_benchmarking.ipynb`

Expert-validation outputs should be added here only after independent expert review has been completed.
