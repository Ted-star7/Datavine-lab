# DataVine Analytics — ML Prototype Suite

A set of three machine-learning prototypes built for a boutique consulting group,
each solving a different client problem: classifying wines, recommending animal
feeds, and finding regional crime patterns. The project takes each dataset through
the full ML workflow — EDA, preprocessing, modelling, evaluation, and interpretation
— and consolidates the results into a single stakeholder report.

## Features

- **Wine classification** — predicts a wine's cultivar from its chemical profile using k-NN, tuned with PCA and GridSearchCV.
- **Feed recommendation** — suggests similar animal feeds using PCA and cosine similarity over feed weight profiles.
- **Crime clustering** — groups US states by crime profile using K-Means and Gaussian Mixture Models, with the optimal cluster count chosen via the elbow method and BIC.
- **Consolidated evaluation** — a final notebook that confirms every dataset, pulls each model's key results together, and summarizes insights for a non-technical client.

## Tech Stack

| Technology | Role in this project |
|------------|----------------------|
| **Python** | Core language for all analysis. |
| **pandas / numpy** | Loading, cleaning, and manipulating the datasets. |
| **scikit-learn** | All ML: `StandardScaler`, `PCA`, `KNeighborsClassifier`, `GridSearchCV`, `KMeans`, `GaussianMixture`, cosine similarity, and metrics. |
| **matplotlib / seaborn** | EDA plots, elbow/BIC curves, and cluster visualizations. |
| **Jupyter notebooks (via VSCode)** | Interactive workflow; each team member owns one notebook. |
| **Git + GitHub** | Version control and team collaboration via protected `main` +  reviews. |

## Architecture

Each task is an independent pipeline that reads from the shared `data/` folder.
Results flow into the integration notebook for the final report.

```
                 ┌─────────────────────────┐
                 │        data/            │
                 │  wine · chickwts ·      │
                 │      USArrests          │
                 └───────────┬─────────────┘
                             │  pd.read_csv()
              ┌──────────────┼──────────────┐
              │              │              │
        ┌─────▼─────┐  ┌─────▼─────┐  ┌─────▼──────┐
        │ Notebook 1│  │ Notebook 2│  │ Notebook 3 │
        │  Wine     │  │  Feed     │  │  Arrests   │
        │  k-NN+PCA │  │ PCA+cosine│  │ KMeans/GMM │
        └─────┬─────┘  └─────┬─────┘  └─────┬──────┘
              │              │              │
              └──────────────┼──────────────┘
                             │  results / metrics
                 ┌───────────▼─────────────┐
                 │      Notebook 4         │
                 │ Integration &           │
                 │ Evaluation (report)     │
                 └─────────────────────────┘
```

## Project Structure

```
.
├── data/                 # Datasets, committed so everyone runs identical data
│   ├── wine.csv          #   178 wines × 13 chemical features + cultivar label
│   ├── chickwts.csv      #   71 chicks: weight by feed type
│   └── USArrests.csv     #   50 US states: Murder, Assault, UrbanPop, Rape
├── notebooks/            # One notebook per person — keeps work conflict-free
│   ├── 01_wine_classification.ipynb    # Dennis — k-NN classification
│   ├── 02_feed_recommendation.ipynb    # Jeff   — recommendation engine
│   ├── 03_arrests_clustering.ipynb     # Eglen & Teddy — clustering
│   └── 04_integration_evaluation.ipynb # Teddy  — consolidated report
├── requirements.txt      # Pinned dependencies for a reproducible environment
├── .github/              # CODEOWNERS + pull-request template for reviews
└── README.md
```

Every notebook currently holds only its **title and rubric checklist** (the
checklist maps 1:1 to the grading rubric). Each owner fills in their own cells —
inspect → standardize → model → evaluate → interpret — inside their notebook.

## Installation & Setup

**Prerequisites:** Python 3.10+, Git, and VSCode with the *Python* and *Jupyter* extensions.

```bash
# 1. Clone
git clone https://github.com/Ted-star7/Datavine-lab.git
cd Datavine-lab

# 2. Create and activate a virtual environment
python -m venv .venv
# Windows:        .venv\Scripts\activate
 **Anaconda users:** you can skip the virtual-environment steps above and simply
 select your existing `base` (conda) environment as the kernel in VSCode — it
 already includes pandas, numpy, scikit-learn, matplotlib and seaborn. Run
 `pip install -r requirements.txt` only if a package turns out to be missing.

# 3. Install dependencies
pip install -r requirements.txt
```

Then open the folder in VSCode, open a notebook in `notebooks/`, select the `.venv`
interpreter in the kernel picker, and run the cells. There are no environment
variables or database configuration — all data is local CSV files in `data/`.

## Usage

1. Open a task notebook in VSCode (e.g. `notebooks/01_wine_classification.ipynb`).
2. Run the imports cell.
3. Load data with `pd.read_csv('../data/wine.csv')` and run each section top to bottom: inspect → standardize → model → evaluate.
4. Follow the markdown checklist at the top — it maps 1:1 to the grading rubric.


## Data Reference

| Dataset | Rows | Key columns | Used for |
|---------|------|-------------|----------|
| `wine.csv` | 178 | `Wine` (label 1-3) + 13 chemical features | k-NN classification |
| `chickwts.csv` | 71 | `weight`, `feed` | feed recommendation |
| `USArrests.csv` | 50 | `Murder`, `Assault`, `UrbanPop`, `Rape`, `State` | clustering |




