# Shodh_AI_project
# Credit Decisioning — DL vs RL
**Assignment for:** Shodh AI (company)  
**Author:** Saksham Goyal

## Repository structure
```
/                   <- root
├── data/           <- raw and processed datasets (do NOT include sensitive PII)
│   ├── raw.csv
│   └── processed.csv
├── notebooks/      <- Jupyter notebooks for EDA, DL model, RL agent
│   ├── 01_EDA.ipynb
│   ├── 02_DL_Model.ipynb
│   └── 03_RL_Agent.ipynb
├── scripts/        <- reproducible scripts (.py) to run experiments
│   ├── train_dl.py
│   ├── evaluate_dl.py
│   ├── train_rl.py
│   └── evaluate_rl.py
├── models/         <- saved model artifacts (weights, checkpoints)
├── results/        <- saved metrics, plots, and analysis CSVs
├── README.md       <- this file
├── requirements.txt
└── Final_Report.pdf
```

## Quick setup (using virtualenv)
```bash
python -m venv venv
source venv/bin/activate   # or `venv\Scripts\activate` on Windows
pip install -r requirements.txt
```

## Suggested `requirements.txt`
```
numpy
pandas
scikit-learn
matplotlib
seaborn
torch
tensorflow
stable-baselines3
gym
d3rlpy   # optional for offline RL evaluation
reportlab
jupyterlab
```

## How to reproduce (high-level)
1. Place raw data into `data/raw.csv`. Keep any PII out of public repo.
2. Run EDA notebook: `notebooks/01_EDA.ipynb` or `scripts/prepare_data.py` to create `data/processed.csv`.
3. Train DL model:
   - Notebook: `notebooks/02_DL_Model.ipynb` (contains model architecture, training loop)
   - Script: `python scripts/train_dl.py --data data/processed.csv --out models/dl_model.pt`
4. Evaluate DL model:
   - `python scripts/evaluate_dl.py --model models/dl_model.pt --data data/processed.csv --out results/dl_metrics.json`
   - Key metrics: **AUC** and **F1-Score** (see evaluate script for exact computation)
5. Train RL agent:
   - Notebook: `notebooks/03_RL_Agent.ipynb` or `python scripts/train_rl.py`
   - Save policy to `models/rl_policy.zip`
6. Evaluate RL agent using Off-Policy or On-Policy evaluation to compute **Estimated Policy Value**:
   - `python scripts/evaluate_rl.py --policy models/rl_policy.zip --data data/processed.csv --out results/rl_metrics.json`

## Files to include in PR / submission
- `notebooks/` (cleaned, runnable notebooks)
- `scripts/` (scripts to reproduce experiments)
- `README.md` and `requirements.txt`
- `Final_Report.pdf` (2–3 page concise report)
- `models/` (or instructions how to download large weights separately)
- `results/` (containing final metrics, confusion matrices, and sample decision examples)

## Repro tips
- Fix randomness with seeds for numpy, torch, tensorflow, gym.
- Keep a small sample dataset `data/sample.csv` for quick CI runs.
- Provide a `Makefile` or `run_all.sh` that runs the entire pipeline end-to-end (prep -> train -> evaluate).

## Contact
Saksham Goyal — submitter for Assignment for Shodh AI.
