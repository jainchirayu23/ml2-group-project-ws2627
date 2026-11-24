# ML2 Group Project: <TODO Dataset Name>

Group project for **Machine Learning 2**, Winter Term 2026/27.

> **Deadline:** Saturday, 9 January 2027, 23:55
> **Deliverables:** report as a Jupyter Notebook + 20-minute presentation

## Team

| Name | Main responsibility |
|------|---------------------|
| Krishna | TODO - Data and EDA |
| Ravi | TODO - Neural network |
| Ebna | TODO - Baseline / second model |
| Chirayu | TODO - Evaluation, report, slides |

## Research question

<One sentence: what we predict, from what, and why it matters.>

## Data

- **Source:** <UCI / Kaggle link>
- **License:** <check>
- **Size:** <n> observations, <p> predictors (requirement: n ≥ 500, ideally 1000–2000; p ≥ 5)
- **Target:** <variable>, <regression | binary | multiclass classification>

Raw data goes in `data/raw/`; it is not committed if the license forbids redistribution. See `data/README.md` for how to download it.

## Methods

| Model | Role | Key hyperparameters |
|-------|------|---------------------|
| <e.g. Gradient boosting / Random forest / regularized GLM> | Non-NN method | <...> |
| Multilayer perceptron (PyTorch) | Required ANN | layers, width, lr, weight decay, dropout, optimizer, init |
| <e.g. majority class / mean predictor / logistic regression> | Baseline | — |

## Experimental protocol

- **Split:** stratified Train / Validation / Test split; the test set is touched **once**, at the end.
- **Model selection:** k-fold cross-validation on the training data for HPO.
- **Seeds:** every experiment is repeated over seeds `[0, 1, 2, 3, 4]`; results are reported as mean ± std (error bars).
- **Metric(s):** <e.g. RMSE / MAE for regression; ROC-AUC, F1, log-loss for classification> — chosen because <reason>.
- **NN ablations:** optimizers (SGD, SGD+momentum, Adam, AdamW) × weight init (default, Xavier/Glorot, He/Kaiming).
- **Regularization:** explicit (L2/weight decay, dropout) vs. implicit (early stopping, SGD noise, batch size, LR schedule).
- **Diagnostics:** learning curves (overfitting), calibration (reliability diagram, Brier score), training and inference time.
- **Leakage checks:** all preprocessing (scaling, imputation, encoding) is fit inside the CV pipeline on training folds only.

## Repository structure

```
.
├── report.ipynb          # Final report (graded deliverable)
├── notebooks/            # Exploratory / scratch notebooks
├── src/                  # Reusable code imported by the report
│   ├── data.py           # loading, splitting, preprocessing
│   ├── models.py         # model definitions (incl. PyTorch MLP)
│   ├── train.py          # CV, HPO, training loops, timing
│   └── evaluate.py       # metrics, calibration, plots
├── data/
│   ├── raw/              # original data (git-ignored)
│   └── processed/        # cleaned data (git-ignored)
├── results/              # CV scores, HPO logs, saved metrics (CSV/JSON)
├── figures/              # plots used in report and slides
├── slides/               # presentation
├── references.bib        # bibliography
├── requirements.txt
└── README.md
```

## Reproducing the results

```bash
git clone https://github.com/<org>/<repo>.git
cd <repo>
python -m venv .venv && source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
# download the data into data/raw/ (see data/README.md)
jupyter lab report.ipynb
```

Then run all cells (Kernel → Restart & Run All). Expected runtime: <~X min on CPU>.

## Report structure (matches grading)

1. Introduction and descriptive analysis (4P)
2. Mathematical overview of the methods (4P)
3. Training and optimization (5P)
4. Evaluation and generalization (5P)
5. Bibliography (2P)

## Workflow

- `main` always runs top to bottom; work on feature branches and merge via pull request.
- Clear notebook outputs before committing scratch notebooks (`nbstripout` recommended); `report.ipynb` is committed with outputs at submission.
- Open an issue for each task and assign an owner.
## References

See `references.bib`; all sources are cited in `report.ipynb`.
