# MIRASH Sarcopenia Calculator

Static browser implementation of the **frozen MIRASH sarcopenia formula** evaluated in CHARLS and externally replicated in NHANES.

## Current version

**v2.0.0**

The numerical coefficients are unchanged from the frozen development model. Version 2.0.0 updates the interpretation boundaries, deployment documentation, applicability/QC messaging, and user interface so that the calculator matches the final manuscript framework.

## Intended use

MIRASH is a research screening / risk-enrichment tool for **contemporaneous sarcopenia in adults aged 60 years or older**. It is not a stand-alone diagnosis and does not replace direct assessment of muscle strength, muscle quantity, or physical performance.

The logistic probability returned by the calculator applies only to the **original frozen sarcopenia target**. The post-freeze muscle/sarcopenia phenotype spectrum was used for construct evaluation; the calculator does not provide calibrated probabilities for low strength, low muscle mass, possible sarcopenia, severe sarcopenia, or other secondary phenotypes.

No universal diagnostic or treatment cutoff is proposed.

## Required inputs

- Age, years
- Sex, male=0 / female=1
- Hemoglobin, g/dL
- Platelet count, 10^9/L
- Creatinine, mg/dL
- Total cholesterol, mg/dL
- HDL cholesterol, mg/dL
- Triglycerides, mg/dL
- Uric acid, mg/dL
- C-reactive protein, mg/L
- Glucose, mg/dL
- HbA1c, %

Natural logarithms are applied automatically to **creatinine, triglycerides, CRP, glucose, and HbA1c**. All other laboratory inputs enter the equation on their raw scale.

### Important preprocessing clarification

Legacy internal variable names beginning with `z_` were naming artifacts and **do not indicate z-score standardization**. The final equation does not apply mean/SD or median/IQR centering/scaling.

The frozen median/IQR values from development were used only to define transformed-scale **8-IQR QC/applicability boundaries**. They are not clinical reference intervals and are not formula scaling constants.

## Frozen formula

The web page displays the complete linear predictor equation and computes:

`Probability = 1 / [1 + exp(-LP)]`

The calculator implements the frozen equation exactly and performs no refitting, recalibration, or cut-off optimization.

## Frozen evaluation summary

- CHARLS 2011 nested out-of-fold evaluation: n=3,517; 663 events; AUC ≈ 0.788
- CHARLS 2015 temporal evaluation: n=5,871; 1,028 events; AUC ≈ 0.804
- CHARLS 2015 ultra-strict participant-independent sensitivity: n=3,053; 380 events; AUC ≈ 0.802
- NHANES 1999–2002 confirmed-sarcopenia external construct replication: n=1,982; AUC ≈ 0.772

NHANES is interpreted as a measurement/definition-different external construct replication rather than an identical phenotype validation.

## Repository files

- `index.html` — static GitHub Pages calculator
- `mirash_model.json` — machine-readable frozen model specification and interpretation boundaries
- `validation_cases.csv` — fixed numerical test cases

The page includes three internal self-tests; if any fixed validation case fails, the calculator displays a self-test failure message rather than returning results.

## Privacy

All calculations run locally in the browser. The static page does not transmit, upload, or store entered values.

## Citation

Please cite the final peer-reviewed MIRASH development and multistage evaluation manuscript when available. The formal citation and DOI will be added after publication.

## Disclaimer

This repository is a research implementation aid. Clinical deployment requires independent prospective impact evaluation, appropriate local validation/governance, and standard sarcopenia assessment where clinically indicated.
