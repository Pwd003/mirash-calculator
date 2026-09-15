# MIRASH Sarcopenia Score Calculator

Browser-based implementation of the **MIRASH Sarcopenia Score** (Metabolic–Inflammatory–Renal–Age–Sex–Hematologic), developed in CHARLS and independently evaluated in NHANES.

## Intended use

MIRASH is intended for **screening / risk enrichment for contemporaneous sarcopenia in adults aged 60 years or older**. It is not a stand-alone diagnosis and does not replace formal assessment of muscle strength, muscle quantity, or physical performance.

The study did **not** establish a universal diagnostic or treatment cutoff. The calculator therefore reports a continuous estimated probability and the linear predictor only.

## Calculator

The calculator is implemented as a static HTML/JavaScript application. All calculations are performed locally in the user's browser; entered values are not transmitted or stored.

### Required inputs

- Age, years
- Sex, female=1 / male=0
- Hemoglobin, g/dL
- Platelets, 10^9/L
- Creatinine, mg/dL
- Total cholesterol, mg/dL
- HDL cholesterol, mg/dL
- Triglycerides, mg/dL
- Uric acid, mg/dL
- C-reactive protein, mg/L
- Glucose, mg/dL
- HbA1c, %

Natural logarithms are applied automatically to creatinine, triglycerides, CRP, glucose, and HbA1c.

## Reproducibility

- `index.html` — web calculator
- `mirash_model.json` — machine-readable model specification
- `validation_cases.csv` — fixed numerical validation cases

Built-in reference check:

- Example input produces LP = `-1.699836`
- Estimated probability = `15.4%`

## Version

Current calculator version: **v1.0.0**

The v1.0.0 implementation corresponds to the fixed MIRASH equation evaluated in CHARLS 2015 and NHANES 1999–2002. Any future coefficient change or recalibration should be released as a new version rather than silently replacing this implementation.

## Citation

Please cite the MIRASH development and validation manuscript when available. The formal manuscript citation and DOI will be added after publication.

## Disclaimer

This repository is a research implementation aid. Before clinical deployment, local calibration and prospective impact evaluation are recommended.
