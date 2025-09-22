# CM3070-FINAL-PROJECT
CM3060 Methodology Classification System 

Predicts one of four labels (*case study, design-based, experiment, survey*) from an abstract.  
Includes calibrated probabilities and an abstention policy (coverage ↔ accuracy).

## Repo structure

.
├── FYP_prototype.ipynb
├── data/                # put your CSV here (not committed)
├── results/             # saved split indices, tables
├── artifacts/           # saved pipeline + meta.json
├── requirements.txt
└── README.md

## Prerequisites
- Python 3.11 (or your version)
- Install deps:

## Here’s a quick start.
How to use FYP_prototype.ipynb
	1.	Set up
	•	Python 3.11+
	•	pip install -r requirements.txt (or conda env create -f environment.yml)
	2.	Add data
	•	Put your CSV at data/abstracts.csv with columns:
abstract (text), label (case study | design-based | experiment | survey).
	•	If names differ, edit the first “Setup” cell: TEXT_COL, LABEL_COL (and ACTIVE_TEXT_COL if you use a cleaned column).
	3.	Run the notebook (top → bottom)
	•	Load data → prints row counts.
	•	Stratified split (80/20, seeded) → saves results/split_indices.json + results/meta.json; shows a per-class split summary.
	•	Tuning → runs small CV grids for NB/LR/LinearSVM (train-only).
	•	Model comparison → picks best_model and best_proba_model.
	•	Hold-out evaluation → classification report + confusion matrix.
	•	Reliability + Brier → probability quality plots (saved to figs/).
	•	Coverage ↔ accuracy → saves results/coverage_accuracy.csv.
	4.	Package & reuse
	•	Run the “Save artifacts & helpers” cell → writes
artifacts/best_pipeline.joblib and artifacts/meta.json.
	•	In-notebook quick test:

predict_one("This paper reports a controlled experiment...", threshold=0.8)
predict_batch(["abstract 1", "abstract 2"], threshold=0.75)


	•	Outside the notebook:

from joblib import load
pipe = load("artifacts/best_pipeline.joblib")
pipe.predict(["short abstract text here"])


	5.	Reproducibility
	•	To reconstruct the exact TRAIN/TEST later, run the “View persisted split + meta” cell; it reloads indices from results/ and rebuilds X_train_text, X_test_text, y_train, y_test.
	6.	Where outputs land
	•	Tables/CSVs → results/ (e.g., best_model_holdout_summary.csv, coverage_accuracy.csv, split_indices.json, meta.json)
	•	Figures → figs/ (SVG + 300-dpi PNG) 
	•	Final model → artifacts/best_pipeline.joblib

That’s it: run top to bottom for full repro, or jump straight to Model comparison, Reliability, and Coverage if artifacts/splits already exist.
