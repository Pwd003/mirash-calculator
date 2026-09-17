# MIRASH Seven-Output Research Calculator

Static GitHub Pages implementation of the **frozen MIRASH core score with seven original CHARLS 2011-frozen outcome-specific mapping heads**.

## Current version

**v3.0.0**

Version 3.0.0 upgrades the calculator from a single sarcopenia output to seven prespecified outputs while preserving the frozen MIRASH core coefficients. The default calculator equations are the original CHARLS 2011-frozen heads. CHARLS 2015 recalibration analyses are secondary model-updating sensitivities and are not used as default equations.

## Target population

Adults aged **60 years or older**.

## Inputs

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

Natural logarithms are applied automatically to **creatinine, triglycerides, CRP, glucose, and HbA1c**. No z-score, mean/SD, or median/IQR standardization is applied. Historical analytic `z_` prefixes were naming artifacts only.

## Seven outputs

1. Handgrip strength — auxiliary continuous research estimate
2. SMI — auxiliary muscle-mass construct estimate
3. Low muscle strength — secondary research probability
4. Low estimated muscle mass — secondary research probability
5. Possible sarcopenia — exploratory probability only
6. Sarcopenia — **primary MIRASH probability output**
7. Severe sarcopenia — secondary severity research probability

The calculator returns continuous values/probabilities only. **No diagnostic, treatment, or risk cutoff is optimized or recommended.**

## Interpretation boundaries

The two continuous mappings are research estimates and must not be treated as substitutes for direct grip testing or DXA/BIA muscle-mass measurement. The low-strength, low-mass, possible-sarcopenia, and severe-sarcopenia probability heads were developed after the MIRASH core score was frozen and should be interpreted according to their stated research roles. Possible sarcopenia remains exploratory because weak temporal discrimination persisted after recalibration. Sarcopenia remains the primary probability output because it was the original frozen development target.

## Model governance

- MIRASH core coefficients: unchanged
- Seven outcome-specific heads: developed in CHARLS 2011 and frozen
- CHARLS 2015: later-wave temporal evaluation
- 2015 recalibration: secondary sensitivity/model-updating audit only
- DCA: prespecified threshold range 0.05–0.40; no threshold selection
- NHANES 1999–2002: independent construct replication with complex-survey methods and five official DXA completed datasets

## Repository files

- `index.html` — static seven-output calculator
- `mirash_model.json` — machine-readable frozen model specification
- `validation_cases.csv` — fixed numerical test cases for all seven outputs

The page performs internal numerical self-tests against fixed validation cases. If the tests fail, the footer reports failure and the implementation should not be used.

## Privacy

All calculations run locally in the browser. The page does not transmit, upload, or store entered patient values.

## Research-use disclaimer

MIRASH does not replace formal sarcopenia assessment or clinical judgment. Clinical deployment would require additional local validation, prospective impact evaluation, and appropriate governance.

## Citation

Please cite the final peer-reviewed MIRASH development and multistage evaluation manuscript when available.
