\# Code Availability Statement



The code supporting the study \*\*A public-data-driven, taxonomy-enabled capability classification framework for regional manufacturing visibility and partner discovery\*\* is available in this repository.



\## Repository Contents



The repository contains Python scripts and notebooks for the main analytical stages of the study:



\- public website text preprocessing;

\- capability term extraction;

\- RMCT controlled vocabulary and thesaurus construction;

\- company-level capability profile generation;

\- benchmarking against practical baselines;

\- expert-validation metric calculation.



\## Code Location



The main scripts are located in the `code/` folder:



| Script | Purpose |

|---|---|

| `01\_preprocess\_public\_web\_text.py` | Clean and prepare public website text |

| `02\_extract\_capability\_terms.py` | Extract candidate manufacturing capability terms |

| `03\_build\_rmct\_vocabulary.py` | Build the RMCT controlled vocabulary and thesaurus |

| `04\_create\_company\_profiles.py` | Generate company-level RMCT capability profiles |

| `05\_benchmark\_retrieval.py` | Benchmark RMCT against comparison methods |

| `06\_expert\_validation\_metrics.py` | Calculate expert validation metrics |



The notebooks in the `notebooks/` folder provide a transparent workflow for taxonomy construction, website-derived cluster validation and benchmarking.



\## Software Environment



The Python package requirements are provided in:



\- `requirements.txt`

\- `environment.yml`



The analysis was developed using Python 3. Package versions should be recorded in the reproducibility protocol where available.



\## Reproducibility Notes



The code is intended to reproduce the analytical workflow using the derived data shared in this repository. Because full raw and cleaned website texts are not redistributed, some preprocessing steps are documented for transparency but cannot be fully rerun from the original raw scrape using this public repository alone.



The shared derived data allow users to inspect and reproduce the main downstream steps, including:



\- RMCT vocabulary structure;

\- company-level capability profiles;

\- benchmark briefs;

\- aggregate benchmark results;

\- expert-validation calculations, where applicable.



\## Limitations



Some parts of the workflow depend on the original website scrape and local preprocessing files, which are not fully redistributed because of copyright, privacy and website terms-of-use considerations. Where full replication is not possible from public repository files alone, the repository provides derived evidence, document hashes, parameter settings and methodological documentation to support auditability.



\## License



The code in this repository is released under the MIT License unless otherwise stated. Derived research data are provided for research and verification purposes subject to the repository data-use notes.

