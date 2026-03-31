# DDI-PREDICT
Machine learning framework for adverse drug reaction risk prediction in cardiovascular patients- proof of concept using FAERS data
# DDI PREDICT
### A Machine Learning Framework for Adverse Drug Reaction Risk 
### Stratification in Hospitalised Cardiovascular Patients

**Author:** Brenda Koech, BSc Pharmacy  
**Affiliation:** Afia Data  
**Conference:** africaSTEMI Live! 2026, Nairobi, Kenya  

---

## Overview
DDI-PREDICT is a proof-of-concept machine learning model that predicts 
whether a cardiovascular patient will experience a serious adverse drug 
reaction — defined as hospitalisation, a life-threatening event, or death.

This work builds on a prior published study assessing drug-drug interaction 
prevalence among cardiovascular inpatients at Kenyatta National Hospital, 
Kenya. It addresses the gap between interaction *detection* (what current 
tools do) and outcome *prediction* (what clinicians actually need).

---

## Dataset
- **Source:** FDA Adverse Event Reporting System (FAERS) — publicly available
- **Size:** 43,626 cardiovascular adverse event reports
- **Outcome:** Serious ADR (hospitalisation, life-threatening event, death)
- **Outcome rate:** 44.4% — well-balanced for machine learning

---

## Features Used
- Patient age
- Sex
- Polypharmacy count (number of concurrent drugs)
- Individual drug class flags: aspirin, clopidogrel, warfarin, 
  beta-blocker, calcium channel blocker, ACE inhibitor, NSAID, 
  digoxin, diuretic, statin
- High-risk drug pair indicators:
  - Aspirin + Clopidogrel
  - Warfarin + Aspirin
  - Beta-Blocker + Calcium Channel Blocker
  - ACE Inhibitor + NSAID
  - Digoxin + Diuretic

---

## Model
- **Algorithm:** XGBoost Classifier
- **Validation:** 5-fold stratified cross-validation
- **Explainability:** SHAP (SHapley Additive exPlanations)

---

## Results

| Metric | Value |
|--------|-------|
| 5-Fold CV AUC-ROC | 0.652 ± 0.006 |
| Test Set AUC-ROC | 0.646 |
| Specificity (low-risk patients cleared) | 81% |

### Top Predictors (SHAP Analysis)
1. Patient Age
2. Polypharmacy Count
3. Statin Exposure

![SHAP Feature Importance](shap_importance.png)
![ROC Curve](roc_curve.png)

---

## Limitations
- FAERS records an average of 1.9 drugs per case — real inpatient 
  records contain richer polypharmacy profiles
- No comorbidity or laboratory data available in this dataset
- Model trained on global reports — local Kenyan validation is the 
  next step

---

## Next Steps
Contextual adaptation using locally collected Kenyan cardiovascular 
inpatient data is planned as part of a forthcoming MSc in Health Data 
Science at the University of Bristol. Multi-site African collaboration 
is invited.

---

## How to Run
1. Open `DDIPREDICT.ipynb` in Google Colab
2. Download FAERS quarterly data from: 
   https://fis.fda.gov/extensions/FPD-QDE-FAERS/FPD-QDE-FAERS.html
3. Upload DEMO, DRUG, REAC, and OUTC files when prompted
4. Run all cells in sequence

---

## Citation
If referencing this work, please cite:
Koech B. (2026). DDIPREDICT: A Machine Learning Framework for Adverse 
Drug Reaction Risk Stratification in Hospitalised Cardiovascular Patients. 
Presented at africaSTEMI Live! 2026, Nairobi, Kenya.

---

## Conflict of Interest
The author declares no conflicts of interest.

---

## Contact
koechi.ict@gmail.com
