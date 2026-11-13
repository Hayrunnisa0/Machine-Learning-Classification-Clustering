# Breast Cancer Wisconsin and Wine Classification — Reproducible Experiments

Repository URL: **ADD YOUR GITHUB REPOSITORY URL HERE** (not supplied; do not submit this placeholder).

## Environment

Python 3.13.5 (tested). Install: `python -m pip install -r requirements.txt`.

Exact package versions are pinned in `requirements.txt`. VS Code with Jupyter support or Jupyter Notebook can open `.ipynb` files.

## Run

From the repository root, run `jupyter notebook` and open `breast_cancer_experiment.ipynb` and `wine_experiment.ipynb`; choose **Run All** in each. Notebook code recreates the original per-dataset CSV files and `figures/` PNG files. The six combined submission CSVs and `report.docx` correspond to the executed notebook outputs committed here; regenerate these combined files if you change notebook experiments.

## Datasets

- Breast Cancer Wisconsin (Diagnostic): https://scikit-learn.org/stable/modules/generated/sklearn.datasets.load_breast_cancer.html — original labels 0=malignant, 1=benign.
- Wine recognition: https://scikit-learn.org/stable/modules/generated/sklearn.datasets.load_wine.html — original labels 0, 1, 2.

## Experiment protocol

Fixed stratified test 20% with random_state=42. For each seed 42, 52, 62, remaining 80% is split 87.5% train / 12.5% validation (about 70/10/20 overall). Raw and StandardScaler-scaled representations are evaluated independently. 132 classification grid fits plus 12 K-Means grid fits = 144 required experimental fits. Final seed-42 test models and seed-42 figure reproductions are additional refits, not extra grid configurations. Hyperparameters are selected using mean validation macro F1 only (AUC tie-break). Scalers fit on training data only. Cluster IDs are not class labels.

## Six required combined CSVs

- `classifier_runs.csv`: 132 rows, individual classifier fits.
- `classifier_summary.csv`: 44 rows, validation means and sample SDs.
- `classifier_test.csv`: 2 rows, seed-42 final held-out test evaluation.
- `kmeans_runs.csv`: 12 rows, individual cluster fits.
- `kmeans_summary.csv`: 4 rows, across-seed means, sample SDs, valid-score counts.
- `kmeans_test.csv`: 4 rows, seed-42 held-out cluster evaluation.

Additional dataset-specific CSVs provide traceability and descriptive statistics. `figures/` contains 21 PNG files. `report.docx` is the formatted report. Full source code lives in notebooks. See `AI_DISCLOSURE.md`.
