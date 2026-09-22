# MIRASH Sarcopenia Research Calculator

Static GitHub Pages implementation of the final frozen **MIRASH** model.

## Current version

**v7.0.0**

The calculator uses seven inputs: age, sex, hemoglobin, HDL-C, triglycerides, uric acid, and C-reactive protein. The final quadratic uric-acid specification was developed in CHARLS 2011, temporally validated in CHARLS 2015, and externally transported to NHANES 1999–2002.

## Primary output

The page reports:
- MIRASH linear predictor
- model-estimated sarcopenia probability
- screen-positive/high-risk classification

## Frozen screen-positive operating point

The development-derived Youden J cutoff is:

- exact probability cutoff: **0.148374094750412**
- equivalent MIRASH LP cutoff: **-1.74741060024184**
- human-readable display: **approximately 15%**

The exact cutoff is used internally. It was applied unchanged in CHARLS 2015 and NHANES and was not re-optimized in either validation setting.

A positive result is a **case-finding trigger** for confirmatory sarcopenia assessment. It is **not** a stand-alone diagnosis or treatment threshold. A negative screen does not exclude sarcopenia when clinical suspicion is present.

## Inputs

- Age, years
- Sex, male=0 / female=1
- Hemoglobin, g/dL (g/L accepted and converted)
- HDL cholesterol, mg/dL (mmol/L accepted and converted)
- Triglycerides, mg/dL (mmol/L accepted and converted)
- Uric acid, mg/dL (µmol/L accepted and converted)
- C-reactive protein, mg/L (mg/dL accepted and converted)

Natural logarithms are applied to triglycerides and CRP. Uric acid enters as a centered quadratic term around 4.4520001411438 mg/dL. No z-score standardization is used.

## Validation summary

- CHARLS 2011 development: N=3,517; 663 cases; repeated OOF AUC 0.783
- CHARLS 2015 temporal validation: N=5,871; 837 cases; AUC 0.807 (95% CI 0.791–0.822)
- NHANES 1999–2002 external transportability: N=1,982; 363–368 cases across DXA completed datasets; AUC 0.768 (95% CI 0.733–0.799)

At the exact frozen cutoff:
- CHARLS 2015 sensitivity 81.0%, specificity 61.5%, NPV 95.1%
- NHANES survey-weighted pooled sensitivity 75.5%, specificity 61.6%, NPV 91.9%

## Phenotype framework

Six additional muscle-health phenotypes were evaluated at the cohort level to characterize what the common MIRASH score captures. They are not deployed as six separate patient-level probability calculators.

## Privacy

All calculations run locally in the browser. The page does not transmit, upload, or store entered values.

## Research-use disclaimer

MIRASH does not replace formal sarcopenia assessment or clinical judgment. Screen-positive individuals should proceed to confirmatory assessment using the applicable sarcopenia diagnostic pathway.

## Repository files

- `index.html` — static calculator
- `mirash_model.json` — machine-readable final model and threshold specification
- `validation_cases.csv` — fixed numerical self-test cases

## Citation

Please cite the final peer-reviewed MIRASH development and multistage evaluation manuscript when available.
