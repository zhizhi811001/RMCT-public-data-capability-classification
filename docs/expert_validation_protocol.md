# Expert Validation Protocol

This document describes the planned independent expert validation procedure for the RMCT public-data capability classification study.

## 1. Purpose

The purpose of expert validation is to assess whether RMCT capability labels assigned from public website evidence are supported by the evidence shown to independent expert reviewers.

This validation is designed to strengthen the credibility of the RMCT company-level capability profiles and to identify ambiguous or false-positive capability assignments.

## 2. Validation Unit

The validation unit is a firm-capability evidence item:

```text
company + evidence span + assigned RMCT capability label
```

Experts are not asked to infer every possible capability of a firm. They are asked only to judge whether the supplied evidence span supports the assigned RMCT label.

## 3. Validation Sample

The sample is designed to cover all eight RMCT dimensions and different levels of website evidence quality.

The current template includes 120 validation items, with 15 items sampled from each RMCT dimension where available. The sample includes both complete/rich websites and partial/short websites to test whether evidence quality affects classification reliability.

## 4. Materials Provided to Experts

Each expert receives a table containing:

- validation item ID;
- anonymised company ID;
- SIC code;
- regional folder / sector grouping;
- website quality flag;
- assigned RMCT dimension;
- assigned narrower category;
- assigned preferred label;
- matched evidence variant;
- short website evidence span;
- blank rating fields.

The public repository template does not include completed expert ratings.

## 5. Expert Task

For each validation item, experts should answer:

> Does the evidence span support the assigned RMCT capability label?

Experts should judge only the evidence provided in the row. If the evidence is insufficient, ambiguous or only indirectly related, this should be recorded.

## 6. Rating Options

Recommended rating options are:

| Rating | Meaning |
|---|---|
| Yes | The evidence clearly supports the assigned RMCT label. |
| No | The evidence does not support the assigned RMCT label. |
| Unclear | The evidence is ambiguous, indirect or insufficient. |

Experts should also provide a confidence rating:

| Confidence | Meaning |
|---|---|
| High | The decision is clear from the evidence span. |
| Medium | The decision is likely but not fully certain. |
| Low | The evidence is weak, ambiguous or difficult to interpret. |

## 7. Corrections and Notes

Experts may optionally suggest:

- a corrected preferred label;
- a corrected RMCT dimension;
- notes explaining ambiguous or false-positive cases.

Corrections are used for diagnostic analysis and possible taxonomy refinement. They are not treated as automatic changes to the RMCT vocabulary.

## 8. Number of Experts

At least two independent experts should complete the validation independently. Experts should not discuss items before submitting their ratings.

## 9. Agreement and Reliability Metrics

After expert ratings are completed, the following metrics may be calculated:

- raw agreement rate;
- Cohen's kappa for two-rater agreement;
- Krippendorff's alpha where appropriate;
- precision by RMCT dimension;
- proportion of unclear cases;
- false-positive examples;
- ambiguous evidence categories.

## 10. Adjudication

Disagreements between experts may be reviewed by a third adjudicator.

Adjudication categories are:

| Category | Meaning |
|---|---|
| Supported | Evidence supports the assigned label. |
| Not supported | Evidence does not support the assigned label. |
| Ambiguous | Evidence is not sufficient for a confident decision. |

The adjudication stage should preserve notes on difficult cases, especially where public website language is vague or multi-interpretable.

## 11. Interpretation

Expert validation assesses whether RMCT assignments are supported by public website evidence. It does not assess whether the firm truly has the capability in operational practice.

Therefore, a negative or unclear expert judgement means that the supplied public evidence does not support the assigned label. It does not necessarily mean that the firm lacks the capability.

## 12. Data Sharing

Completed expert judgements are not included in the current repository template. They may be added after the validation stage is completed, subject to consent and data-governance considerations.

The public template contains evidence spans and assigned labels only. It does not contain full raw website HTML or full cleaned website text.
