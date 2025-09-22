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

**pip**
```bash
python -m venv .venv && source .venv/bin/activate   # Windows: .\.venv\Scripts\activate
pip install -r requirements.txt
