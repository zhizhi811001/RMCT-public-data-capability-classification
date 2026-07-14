# Supplementary Material S1. Methodological Completion and Reproducibility Record

This supplementary material documents the data extraction window, software environment, text-processing rules, clustering settings, matching logic and manual decisions used to construct the RMCT public capability observability dataset. Items marked as `To confirm` should be verified against the original scraper or final Colab notebook before journal submission.

## S1.1 Data sources and extraction window

| item | value | source | interpretation |
| --- | --- | --- | --- |
| SIC-defined regional manufacturer frame | 4,462 firms | Manuscript / Companies House-derived frame | Defines total regional population before website linkage. |
| Verified manufacturer URLs | 1,043 firms | Manufacturer URL collection | Firms with identified public websites. |
| Usable website text corpus | 888 firms | Step2b_public_website_corpus_corrected.xlsx / public_company_frame_sample.csv | Company-level corpus used for RMCT profiling. |
| Crawler/extraction date window | 2026-06-03 18:23 to 2026-06-04 10:05 | preprocessing metadata workbook | Time window recovered from scraped text metadata; verify timezone/source before final submission. |
| Final RMCT preferred labels | 433 | Step7_Final_RMCT_taxonomy_and_vocabulary.xlsx | Final controlled vocabulary concepts. |
| Total unique searchable strings | 486 | Vocabulary reconciliation audit | 433 preferred labels plus 53 non-preferred alternative strings. |

## S1.2 Website text status and quality counts

Company-level website text status in the public reproducibility dataset:

| status | n_companies |
| --- | --- |
| SUCCESS | 804 |
| PARTIAL | 84 |

Company-level website quality flags:

| quality_flag | n_companies |
| --- | --- |
| usable_rich | 556 |
| usable | 248 |
| short_but_usable | 79 |
| very_short | 5 |

## S1.3 Software environment

| software_or_package | version | source | status |
| --- | --- | --- | --- |
| Python | 3.12.13 | Bundled local runtime used for repository checks | Recorded |
| pandas | 3.0.1 | Bundled local runtime used for repository checks | Recorded |
| NumPy | 2.3.5 | Bundled local runtime used for repository checks | Recorded |
| openpyxl | 3.1.5 | Bundled local runtime used for Excel generation | Recorded |
| matplotlib | 3.11.0 | Bundled local runtime used for figure/script checks | Recorded |
| scikit-learn | Not installed in local bundled runtime; used in Colab/project scripts where applicable | Recover from final Colab environment | To confirm |
| sentence-transformers | Not installed in local bundled runtime; model recorded as all-MiniLM-L6-v2 | Colab clustering environment | To confirm package version |
| umap-learn | Not installed in local bundled runtime | Colab clustering environment | To confirm package version |
| hdbscan | Not installed in local bundled runtime | Colab clustering environment | To confirm package version |

The deterministic repository scripts were checked using the local bundled Python runtime. The final Sentence-BERT, UMAP and HDBSCAN package versions should be confirmed from the final Colab environment because those packages were not installed in the local bundled runtime used for repository packaging.

## S1.4 Pipeline parameters and thresholds

| stage | parameter | value | source | status |
| --- | --- | --- | --- | --- |
| Text cleaning | Character and whitespace normalisation | HTML unescape; Unicode NFKC; remove URLs, e-mail addresses and phone-like strings; collapse whitespace | preprocess_scraped_texts.py / methodology workbook | Recorded |
| Text cleaning | Sentence retention | sentence length >= 25 characters; alphabetic character ratio >= 0.35 | preprocess_scraped_texts.py / methodology workbook | Recorded |
| Text quality flag | very_short | < 80 word-like tokens | preprocess_scraped_texts.py / methodology workbook | Recorded |
| Text quality flag | short | 80-199 word-like tokens | preprocess_scraped_texts.py / methodology workbook | Recorded |
| Text quality flag | usable | >= 200 word-like tokens after cleaning | preprocess_scraped_texts.py / methodology workbook | Recorded |
| Text quality flag | heavy_noise_removed | clean/raw character ratio < 0.25 | preprocess_scraped_texts.py / methodology workbook | Recorded |
| Text quality flag | many_duplicates_removed | duplicate sentences >= 10 | preprocess_scraped_texts.py / methodology workbook | Recorded |
| Literature concept extraction | Raw concepts | Approximately 1,500 capability-related expressions from 62 references | Literature concept audit | Recorded |
| Literature concept cleaning | Final clustering input | 373 cleaned concept phrases retained after removing metadata, OCR fragments, generic terms and non-capability concepts | cluster_input_cleaned_phrases.csv | Recorded |
| Literature embedding | Sentence-BERT model | all-MiniLM-L6-v2 | Final manuscript protocol | Recorded; package version to confirm |
| Literature UMAP | Final visualisation parameters | n_neighbors=20; min_dist=0.08; random_state=42 recommended/assumed for final rerun | Final cluster file name and protocol notes | Partly recorded; seed to confirm |
| Literature HDBSCAN | Final clustering parameters | min_cluster_size=8; min_samples=3; residual label=-1 retained as noise | RMCT_HDBSCAN_n20_d008_mcs8_ms3 output | Recorded |
| Website n-gram extraction | n-gram range | 1-4 word candidate phrases | 02_extract_capability_terms.py | Recorded |
| Website n-gram extraction | minimum document frequency | min_df=3 | 02_extract_capability_terms.py | Recorded |
| Website n-gram extraction | maximum features | max_features=10000 | 02_extract_capability_terms.py | Recorded |
| Website candidate filtering | manufacturing context terms | manufacturing, machining, fabrication, casting, forming, welding, assembly, material, quality, certification, engineering, prototype, production, coating, testing, inspection, automation, supply | 02_extract_capability_terms.py | Recorded |
| Website concept selection | diverse candidate set | 700 website-derived concepts selected using relevance scoring and MMR-style diversity selection | Final manuscript protocol / Colab run | Recorded concept count; exact MMR lambda to confirm |
| Website embedding | Sentence-BERT model | all-MiniLM-L6-v2 | Final manuscript protocol | Recorded; package version to confirm |
| Website clustering | Final result | 9 non-noise clusters plus residual noise group -1 | Final manuscript protocol / website cross-check figure | Recorded result; exact UMAP/HDBSCAN parameters to confirm from Colab |
| Controlled vocabulary | Preferred labels | 433 final preferred labels | Step7 final vocabulary | Recorded |
| Controlled vocabulary | Alternative-label mappings | 477 row-level mappings; 53 non-preferred unique alternative strings | Vocabulary reconciliation audit | Recorded |
| Matching | Phrase matching rule | Exact phrase boundary matching after lower-case and whitespace normalisation; pattern uses non-alphanumeric boundaries | 04_create_company_profiles.py | Recorded |

## S1.5 Matching, negation and ambiguity rules

| rule_area | documented_rule | risk_or_limitation | submission_action |
| --- | --- | --- | --- |
| Matching rules | Preferred labels and alternative labels are normalised and matched against cleaned company website text using deterministic exact phrase boundary matching. | May miss paraphrases not present in the vocabulary; this motivates BM25/dense/LLM baselines. | Report as deterministic lexical matching. |
| Negation handling | No automated negation detection was applied in the original matching pipeline. | Statements such as 'we do not provide X' may produce false positives, although manufacturer capability pages typically advertise rather than deny services. | State as limitation; check false positives during expert validation. |
| Ambiguity handling | Ambiguous and generic terms were screened during vocabulary construction and could be marked as review, merged, excluded or retained as regional/emerging. | Generic terms such as quality, engineering, energy or delivery may require surrounding context. | Use expert validation categories Yes / No / Unclear and report ambiguous examples. |
| Manual taxonomy decisions | Literature clusters were interpreted and consolidated into facets where clusters represented subtypes of broader capabilities. | Manual interpretation introduces researcher judgement. | Provide manual decision log and empirical website-cluster cross-check. |
| Engineering vs R&D boundary | Engineering and industrialisation support includes DFM, prototyping, testing, NPI and production engineering. Formal R&D should only be coded where stronger website evidence appears. | Avoids overclaiming R&D capability from generic innovation wording. | Require evidence such as research facilities, patents, funded R&D programmes, experimental development, technology maturation, dedicated R&D team or proprietary process development. |
| SSL/certificate bypass treatment | Original scraper SSL/certificate handling is not fully recorded in the current processed corpus. | Reviewers may ask whether certificate verification was bypassed or whether access restrictions were ignored. | Recover original scraper settings; if unavailable, report as not captured and exclude blocked/failed claims from analysis. |

## S1.6 SUCCESS, PARTIAL, FAILED and BLOCKED definitions

| status | definition | observed_count_or_source | reporting_note |
| --- | --- | --- | --- |
| SUCCESS | Crawler retrieved usable website text and extraction produced substantive content. In the public company frame, SUCCESS is used for company text classified as usable or usable_rich. | 804 company-level records in public_company_frame_sample.csv; 654 crawler SUCCESS records in preprocessing workbook | Distinguish company-level usability from crawler-level status. |
| PARTIAL | Crawler retrieved only limited/subset website text, or company text was short but retained because it contained usable public evidence. In the public company frame, PARTIAL is used for short_but_usable and very_short records. | 84 company-level records in public_company_frame_sample.csv; 234 crawler PARTIAL records in preprocessing workbook | Use in expert sampling to ensure weaker websites are represented. |
| FAILED | No usable website text was retrieved because the site was unreachable, returned errors, or extraction failed. | Not present in usable corpus; recover from original crawl log if available | Report only if full crawl log can be recovered. |
| BLOCKED | Crawler access was prevented by anti-bot controls, authentication, robots restrictions, JavaScript-only access or security challenge pages. | Not present in usable corpus; recover from original crawl log if available | Do not infer capability absence from BLOCKED records. |

## S1.7 Manual taxonomy and classification decisions

| decision_id | decision_area | decision | rationale |
| --- | --- | --- | --- |
| D01 | Exclude methodological cluster | Ontology, semantic web and KG construction terms were excluded from first-level RMCT facets. | They describe modelling methods rather than firm-level manufacturing capabilities. |
| D02 | Merge process subclusters | Machining, forming, fabrication, drilling, coating and related clusters were consolidated under Production Process Capability. | They are process subtypes rather than separate first-level facets. |
| D03 | Merge material subclusters | Metals, ceramics/glass, polymers/composites and material properties were consolidated under Material Capability. | They represent material subcategories within one broader capability facet. |
| D04 | Retain commercial and delivery readiness | Commercial and delivery readiness was retained as a candidate/confirmed facet. | Website clusters showed observable delivery, lead-time, supply-chain and production-scale language relevant to partner discovery. |
| D05 | Retain sustainability as cross-cutting facet | Sustainability and circular production practice was retained as an emerging/cross-cutting facet. | Website evidence exists but overlaps with energy-sector and materials/process language. |
| D06 | Separate engineering support from formal R&D | DFM, prototyping, testing, NPI and production engineering are coded as engineering/industrialisation support; formal R&D requires stronger evidence. | Prevents overclaiming R&D capability from generic innovation wording. |

## S1.8 Controlled-vocabulary count reconciliation

| metric | value | interpretation | calculation |
| --- | --- | --- | --- |
| Preferred-label rows / final RMCT concepts | 433 | Number of final controlled-vocabulary concepts. Each row has one preferred label. | Count rows in Final RMCT Vocabulary / public rmct_controlled_vocabulary.csv. |
| Unique preferred labels | 433 | Unique standard labels after case and whitespace normalisation. | nunique(normalised preferred_label). |
| Alternative-label mapping rows | 477 | Row-level alternative-label links stored in the alternative_labels field. This is a mapping count, not a count of unique alternative terms. | Split alternative_labels by semicolon/pipe and count all resulting row-level mappings. |
| Alternative-label mappings identical to preferred label | 424 | Mappings where the alternative string is the same as the preferred label. These are useful for traceability but do not add a new searchable expression. | Count alternative_label_norm == preferred_label_norm. |
| Alternative-label mappings not identical to preferred label | 53 | Row-level mappings that add a non-preferred spelling, abbreviation or synonymous expression. | Alternative-label mapping rows minus mappings identical to preferred label. |
| Unique alternative-label strings, including strings also used as preferred labels | 477 | Distinct strings appearing in the alternative_labels field after normalisation. | nunique(normalised alternative_label). |
| Unique non-preferred alternative strings | 53 | Distinct alternative strings that are not already preferred labels. | Set(normalised alternatives) minus Set(normalised preferred labels). |
| Total unique searchable strings | 486 | Distinct strings available for matching after combining preferred labels and alternative-label strings. | Union of normalised preferred labels and normalised alternative labels. |
| Concept-to-string mapping count before deduplication | 910 | All row-level links from RMCT concepts to searchable strings, including preferred-label links and alternative-label mappings. | Preferred-label rows + alternative-label mapping rows. |
| Cross-concept duplicate searchable strings | 0 | Searchable strings mapped to more than one preferred label. These should be checked for ambiguity or intentional overlap. | Count searchable_string_norm groups with more than one preferred_label. |

The final RMCT controlled vocabulary contains 433 preferred labels. The alternative-label field contains 477 row-level mappings; this is a mapping count, not a count of 477 distinct alternative terms. Of these mappings, 424 repeat the preferred label for traceability and 53 provide non-preferred variants. Combining preferred labels and non-preferred alternatives yields 486 unique searchable strings.

## S1.9 Reproducibility gaps to close before submission

| item | current_status | needed_before_submission |
| --- | --- | --- |
| Original scraper code and request settings | Not fully available in current workspace | Record crawler library, timeout, user-agent, retry policy, robots handling, JavaScript rendering, SSL verification/bypass policy. |
| Failed/blocked website log | Only usable corpus and unmatched count are currently available | Recover full crawl log to classify SUCCESS, PARTIAL, FAILED, BLOCKED, NO_URL and NO_TEXT. |
| Colab package versions | Final parameter values recorded; exact package versions not fully captured locally | Run pip freeze in final Colab notebook and archive output. |
| Random seeds | Seed 42 recommended and used for final reproducibility package where rerun; original Colab seed should be confirmed | Set random_state=42 for UMAP and all sampling operations in final rerun. |
| MMR selection parameter | 700 selected website concepts recorded; exact diversity lambda should be verified | Recover final Colab cell or rerun with fixed lambda and seed. |

## S1.10 Recommended wording for the manuscript

The website corpus was collected from public manufacturer websites between 2026-06-03 18:23 and 2026-06-04 10:05, based on available scrape metadata. Text was cleaned through HTML decoding, Unicode normalisation, removal of URL, email and phone-like strings, sentence filtering and duplicate/noise screening. Candidate concepts were extracted using one- to four-word n-grams and manufacturing-context filtering. Literature and website concepts were embedded using the all-MiniLM-L6-v2 Sentence-BERT model and clustered using UMAP and HDBSCAN. Controlled-vocabulary matching used deterministic exact phrase-boundary matching over preferred labels and alternative labels. The original pipeline did not implement automated negation detection; ambiguous terms were handled through manual screening, term-status assignment and expert-validation design.
