# Code Availability Statement

The code used to document and reproduce the RMCT public-data workflow is available in the public repository: https://github.com/zhizhi811001/RMCT-public-data-capability-classification. The repository includes scripts for public web-text preprocessing, candidate capability term extraction, controlled vocabulary construction, company profile creation, benchmark calculation and expert-validation metrics.

The repository is intended to support transparent reproduction of the processing logic using either the released derived data or an authorised local website corpus. It does not include full raw website text. Scripts that require full website text expect a local private input file and write only derived or anonymised outputs suitable for public sharing.

The repository also includes environment files, package requirements, notebooks, data availability and ethics statements, a reproducibility protocol, a controlled-vocabulary audit, and expert-validation templates. Software versions recovered from the local reproducibility environment and the Colab-dependent components are reported in the Supplementary Material. Package versions for any final Colab-based Sentence-BERT, UMAP or HDBSCAN reruns should be archived with the final submission using `pip freeze` or an equivalent environment export.
