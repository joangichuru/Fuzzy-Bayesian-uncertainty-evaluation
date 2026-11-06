# Fuzzy–Bayesian uncertainty integration — research code

**Manuscript:** *Evaluating Semantic–Probabilistic Uncertainty Integration in Fuzzy–Bayesian Inference for Potato Blight Disease Prediction*.

## Status
This is a **pre-publication reproducibility package** for author review, not yet a public GitHub release. The original `RevisedBN(4).ipynb` and dataset were not modified. The packaged notebook preserves the original experiment implementations. Only the data-file location and the final grouped-validation fold source were adapted for independent execution.

## Files
- `Fuzzy_Bayesian_Reproducibility.ipynb`: 25 code cells and one empty trailing cell, comprising the experiments and later audit, including a grouped split loaded from a CSV rather than recomputed by the installed scikit-learn version.
- `grouped_folds_historical.csv`: 4,020 test-row-to-fold assignments giving the historical split used for manuscript Tables 8–9.
- `grouped_folds_corrected_reference.csv`: the same rows with test fold assignments from the corrected scikit-learn `StratifiedGroupKFold` for transparency; **not used by the notebook**.
- **Dataset not redistributed**. Download *Potato Leaf Disease Based on Weather Details* from https://www.kaggle.com/datasets/tamima1530/potato-leaf-disease-based-on-weather-details and place the original Excel file in this folder named `Disease with Weather.xlsx` before running the notebook. See `DATA_SOURCE.md`.
- `requirements.txt`: compatible dependency ranges; `environment_tested_here.txt`: packaging test environment versions .

## Running locally
1. Extract this directory and start a terminal in it.
2. Download the original dataset from Kaggle and save the Excel file as `Disease with Weather.xlsx` in the same directory as the notebook.
3. Create a Python environment and install: `python -m pip install -r requirements.txt`.
4. Open `Fuzzy_Bayesian_Reproducibility.ipynb` with Jupyter in this directory.
5. Choose **Kernel → Restart & Run All**. The first cells should find `Disease with Weather.xlsx` and report **4,020** observations (Early Blight 2,066; Late Blight 1,954).
6. Results calculated from pooled out-of-fold scores should be distinguished from averages of individual fold scores. The final prediction-consistency audit resolves a preceding tie-handling mismatch.

## Validation reproducibility and limitation
The saved manuscript's grouped validation was originally produced using the **historical** implementation of `StratifiedGroupKFold(shuffle=True, random_state=42)`. A later scikit-learn bug fix modified fold allocation. The historical test fold sizes were **788, 767, 830, 781, 854**, whereas a corrected implementation yielded **805, 805, 803, 804, 803** in the audit environment.

This notebook loads the historical fold IDs to reproduce the exact manuscript protocol (Tables 8–9) independent of software version. The historical fold assignment enforces exact-weather-pattern separation but has less balanced class proportions than the corrected algorithm. This difference **must not be hidden**: a new study using corrected group allocation reports different grouped performance (see `GROUPED_VALIDATION_NOTE.md`). Historical folds are retained for auditability, 
Historical fold sizes are verified from `grouped_folds_historical.csv` and group leakage checks run before any fitting. 

## Scope
The notebook supports the final BN/fuzzy/hybrid and uncertainty investigations, but exploratory membership function results in manuscript Table 1 require separate historical code for experiments done independently to empirically inform design choices.


-
