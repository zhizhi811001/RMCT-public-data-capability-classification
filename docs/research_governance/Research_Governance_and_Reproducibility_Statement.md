# Research Governance and Reproducibility Statement

## Data release boundary

The public release contains derived and audit-oriented data only. Shared files may include:

- anonymised company identifiers;
- SIC code and regional folder fields;
- website availability and text-status fields;
- crawl-date metadata where available;
- document hashes;
- controlled vocabulary terms;
- preferred labels and alternative-label mappings;
- anonymised company-level RMCT profiles;
- benchmark briefs and aggregate benchmark results;
- expert-validation protocol and sample template;
- short extracted evidence spans where required for expert validation.

The public release does not include:

- full raw website pages;
- full cleaned website text;
- complete scraped HTML;
- personal names, emails, telephone numbers or contact details where detected;
- live operational capacity, prices, quotes or confidential supplier information.

## Personal information handling

Preprocessing included removal of URL strings, email-like strings, phone-like strings and noisy boilerplate where detected. The released data are intended to describe organisational capability evidence, not individual people. Any residual personal information identified during final audit should be removed before repository release or journal submission.

## Website text and copyright

The websites were publicly accessible at the time of collection, but full website text is not redistributed because it remains third-party content subject to copyright, website terms and later source changes. Reproducibility is supported through derived variables, evidence spans, document hashes, source identifiers and code rather than redistribution of full website text.

## Crawl date and source retention

The available scrape metadata indicate a collection window from 2026-06-03 18:23 to 2026-06-04 10:05. Where possible, retained metadata should include company identifier, source URL, crawl date/time, text status, document hash, and extraction status. The source retention procedure is:

1. retain internal raw/cleaned website text only in a secure local research workspace;
2. release only derived public outputs and short evidence spans;
3. retain SHA-256 document hashes to support provenance and duplicate checking;
4. document whether each record was successfully retrieved, partially retrieved, failed, or blocked;
5. do not infer absence of capability from failed, blocked, missing or non-disclosing websites.

## Reproducibility controls

The repository provides scripts, notebooks, requirements files, environment metadata and supplementary methodological tables. Reproducibility records include:

- software and package versions where recoverable;
- Sentence-BERT model name;
- UMAP and HDBSCAN parameters where recorded;
- random seeds where used or recommended for final reruns;
- filtering thresholds;
- matching rules;
- manual taxonomy decisions;
- negation and ambiguity handling rules;
- SUCCESS, PARTIAL, FAILED and BLOCKED definitions.

Any unresolved settings, such as original scraper request settings, SSL/certificate handling, failed/blocked crawl logs, Colab package versions and MMR diversity parameters, should be confirmed before final journal submission and recorded in the Supplementary Material.
