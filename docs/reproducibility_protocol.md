\# Reproducibility Protocol



This document records the methodological steps, parameters and reproducibility notes for the RMCT public-data capability classification study.



\## 1. Overview



The study constructs and evaluates the Regional Manufacturing Capability Taxonomy (RMCT) as a public-data-driven, taxonomy-enabled capability classification framework. The workflow converts public manufacturer website evidence into structured company-level capability profiles for regional manufacturing visibility and partner discovery.



The pipeline includes:



1\. public website text preprocessing;

2\. literature-derived capability concept extraction;

3\. independent website-derived capability concept extraction;

4\. semantic clustering and empirical cross-checking;

5\. controlled vocabulary and thesaurus construction;

6\. company-level capability profile generation;

7\. benchmarking against practical baselines;

8\. expert-validation analysis.



\## 2. Public Website Corpus



The empirical corpus consists of public manufacturer website text collected from firms in the West Midlands manufacturing ecosystem.



Key corpus-level information:



| Item | Description |

|---|---|

| Company population frame | Companies House-derived manufacturer population frame |

| Verified manufacturer URLs | 1,043 firms |

| Usable website texts | 888 firms |

| Website text status categories | SUCCESS / PARTIAL / FAILED / BLOCKED, where available |

| Scraping period | To be reported from scraping log |

| Raw website text sharing | Not shared |

| Cleaned full text sharing | Not shared |

| Derived evidence spans | Shared where appropriate |

| Document hashes | Shared for verification |



The full website corpus is not redistributed because manufacturer websites may be subject to copyright, website terms of use and later modification by website owners.



\## 3. Website Scraping Status Definitions



Where available, website collection outcomes are defined as follows:



| Status | Definition |

|---|---|

| SUCCESS | The website was accessible and sufficient text was extracted for downstream capability analysis. |

| PARTIAL | The website was accessible, but the extracted text was limited, incomplete or only partly usable. |

| FAILED | The website could not be scraped successfully because of access, parsing or technical failure. |

| BLOCKED | The website prevented automated access, for example through blocking, security restrictions or access-control mechanisms. |



These categories are used to distinguish firms with usable website evidence from firms where public website evidence was limited or unavailable.



\## 4. Text Preprocessing



Website text was cleaned before capability extraction. The preprocessing procedure included:



\- lowercasing;

\- whitespace normalisation;

\- removal of repeated boilerplate where detected;

\- removal or exclusion of contact details where detected;

\- removal of email addresses and phone numbers where detected;

\- filtering of very short or low-information text;

\- preservation of capability-relevant phrases.



The preprocessing aimed to retain manufacturing capability signals while reducing noise from navigation menus, repeated footer text, legal notices and contact information.



Full cleaned website texts are not redistributed in this repository.



\## 5. Literature-Derived Concept Extraction



Capability-related concepts were extracted from the reviewed manufacturing capability, supplier discovery, controlled vocabulary, ontology and supply-chain visibility literature.



The extracted concepts were cleaned and normalised before semantic clustering. Concepts describing research methods only, rather than firm-level manufacturing capability, were reviewed and excluded from the final capability dimension structure where appropriate.



The purpose of this stage was to construct a theoretically grounded preliminary RMCT structure.



\## 6. Independent Website-Derived Concept Extraction



Independent website-derived capability concepts were extracted directly from the cleaned public website corpus.



This stage did not use the literature-derived RMCT seed vocabulary as a filter. Its purpose was to provide an empirical cross-check against the literature-derived structure and to identify capability expressions used by manufacturers in public website language.



Candidate concepts were generated from website text using phrase extraction and screening rules. The screening considered:



\- manufacturing relevance;

\- phrase quality;

\- document frequency;

\- contextual evidence;

\- removal of obvious noise terms;

\- avoidance of full website text redistribution.



A diverse set of website-derived capability concepts was then used for semantic clustering and cross-checking against the RMCT dimensions.



\## 7. Semantic Clustering



Semantic clustering was used to identify and cross-check candidate capability dimensions.



The workflow used:



| Step | Method |

|---|---|

| Text representation | Sentence-BERT embeddings |

| Model | `all-MiniLM-L6-v2` |

| Dimensionality reduction | UMAP |

| Clustering | HDBSCAN |

| Visualisation | 2D UMAP plot |



Parameters should be recorded in the final manuscript and supplementary methods. These include:



| Parameter | Value |

|---|---|

| Sentence-BERT model | `all-MiniLM-L6-v2` |

| UMAP `n\_neighbors` | To be reported |

| UMAP `min\_dist` | To be reported |

| UMAP random seed | To be reported |

| HDBSCAN `min\_cluster\_size` | To be reported |

| HDBSCAN `min\_samples` | To be reported |

| HDBSCAN metric | To be reported |



The clustering outputs were interpreted as semantic concept groups. These groups were not treated as final dimensions automatically. Instead, they were reviewed for conceptual coherence, manufacturing relevance and usefulness for supplier discovery.



\## 8. Controlled Vocabulary and Thesaurus Construction



The RMCT controlled vocabulary was constructed after the first-level RMCT dimensions were confirmed.



Each vocabulary entry includes:



\- preferred label;

\- alternative labels;

\- broader RMCT dimension;

\- narrower capability category;

\- source type;

\- evidence counts where available.



The controlled vocabulary is used to normalise heterogeneous website expressions. For example, spelling variants, abbreviations and closely related expressions can be mapped to a standard preferred label.



The controlled vocabulary supports:



\- consistent website evidence matching;

\- company-level capability classification;

\- dimension-level profiling;

\- capability-specific benchmarking;

\- expert validation of assigned capability labels.



\## 9. Company-Level Capability Profiles



For each firm, cleaned website evidence was matched against RMCT preferred labels and alternative labels.



Each company-level profile records:



\- company identifier;

\- detected RMCT preferred labels;

\- narrower capability categories;

\- broader RMCT dimensions;

\- evidence frequency;

\- source evidence spans where available.



These profiles are used for coverage, specificity and benchmarking analyses.



A company profile should be interpreted as a public-data-derived representation of visible capability evidence. It is not a complete operational audit of the firm's real capacity, resources or supplier performance.



\## 10. Benchmarking



RMCT-based classification is compared with practical alternatives. Comparator systems may include:



\- SIC code baseline;

\- keyword-only baseline;

\- single-dimension RMCT baseline;

\- BM25 lexical retrieval baseline;

\- dense embedding retrieval baseline;

\- LLM-assisted retrieval or classification baseline, where applicable.



Main evaluation criteria include:



\### 10.1 Population Coverage



Population coverage assesses whether the method can reach the relevant regional supplier population.



\### 10.2 Capability Specificity



Capability specificity assesses whether the method provides actionable capability descriptors beyond broad sector or activity codes.



\### 10.3 Search Noise Reduction



Search noise reduction assesses whether the method reduces the number of candidate firms that a buyer must manually inspect for multi-dimensional sourcing requirements.



Where expert-labelled relevance judgments are available, additional information-retrieval metrics may be calculated, including:



\- precision;

\- recall;

\- F1 score;

\- precision at k;

\- recall at k;

\- nDCG;

\- MAP;

\- candidate-set reduction at fixed recall.



\## 11. Expert Validation



Expert validation is designed at the firm-capability evidence level.



Experts are asked to judge whether the evidence span supports the assigned RMCT capability label. The validation unit is therefore:



```text

company + evidence span + assigned RMCT capability label
Potential expert-validation metrics include:

agreement rate;

Cohen's kappa;

Krippendorff's alpha;

precision by RMCT dimension;

false positive examples;

ambiguous evidence categories.

Disagreements may be resolved through adjudication by a third reviewer.

Experts do not need to infer every possible capability of a firm. They only judge whether the supplied evidence supports the assigned capability label.


## 12. Random Seeds and Reproducibility

Where stochastic procedures are used, random seeds should be recorded. This includes:

train/test or holdout splits;

sampling of expert-validation cases;

dimensionality reduction where applicable;

clustering where applicable.

Known random seeds should be documented in the relevant scripts and notebooks.

Recommended fields to report include:

Procedure	Random seed

Expert-validation sample selection	To be reported

Holdout split	To be reported

UMAP dimensionality reduction	To be reported

Any sampling of website-derived concepts	To be reported



\## 13. Matching Rules

Website evidence was matched to RMCT vocabulary entries using preferred labels and alternative labels.

The matching procedure should report:

whether matching was case-insensitive;

whether word-boundary matching was used;

whether plural or spelling variants were normalised;

how abbreviations were handled;

how multi-word phrases were matched;

how duplicate matches within the same company were counted;

whether evidence frequency and company frequency were calculated separately.

Where possible, exact phrase matching should be used conservatively to avoid over-matching generic terms.


## 14. Negation and Ambiguity Handling

Website text may contain ambiguous expressions or negated statements. For example, a firm may mention a capability as a sector context, a certification requirement, a previous project, a customer need or a service actually provided.

Ambiguous cases should be handled conservatively. Recommended categories include:

Category	Meaning

Supported	Evidence clearly supports the assigned capability label.

Ambiguous	Evidence may support the label, but the meaning is unclear.

Not supported	Evidence does not support the assigned capability label.



For expert validation, ambiguous cases should be recorded rather than forced into a binary yes/no decision.


## 15. Manual Taxonomy Decisions

Some taxonomy decisions require interpretation, especially when concepts overlap across dimensions.

Manual decisions should be recorded where applicable, including:

merging of similar clusters;

exclusion of methodology-only clusters;

consolidation of process subtypes;

consolidation of material subtypes;

treatment of sustainability as a first-level or cross-cutting dimension;

treatment of commercial and delivery readiness as a supplier-discovery dimension;

synonym merging under preferred labels.

These decisions should be reported transparently so that readers can distinguish algorithmic clustering from researcher interpretation.


## 16. Known Reproducibility Constraints

The repository is designed for auditability and partial reproducibility while respecting copyright and privacy constraints.

The following materials are not publicly redistributed:

full raw website HTML;

full cleaned website text;

complete local scrape archives;

personal contact information.

Therefore, some preprocessing steps cannot be fully rerun from the public repository alone. The repository instead provides derived evidence spans, document hashes, capability labels, company-level profiles, aggregate outputs and methodological documentation.


## 17. Recommended Reproduction Order

A user wishing to reproduce the analysis should follow this order:

inspect data/README\_data.md;

inspect data/rmct\_controlled\_vocabulary.csv;

inspect data/capability\_evidence\_spans.csv;

inspect data/rmct\_company\_profiles\_anonymised.csv;

run code/04\_create\_company\_profiles.py, where compatible input data are available;

run code/05\_benchmark\_retrieval.py;

run code/06\_expert\_validation\_metrics.py, if expert-validation data are available;

compare outputs with files in outputs/tables/ and outputs/figures/.


## 18. Versioning

Repository versions should be tagged at major manuscript stages, for example:

v0.1-submission-draft;

v0.2-revision;

v1.0-publication.

Each release should record the manuscript version, data version and code version.


## 19. Limitations of Reproducibility

This repository supports transparency, auditability and partial reproduction of the analytical workflow. It does not enable complete reconstruction of the original website scrape because full website texts are not redistributed.

Users should interpret the repository as a reproducibility package for derived capability classification outputs, not as a full mirror of the original web corpus.

