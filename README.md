# 🏆 World Cup Final Predictor : Spain vs Argentina

A machine learning project predicting the outcome of the 2026 FIFA World Cup Final between **Spain ** and **Argentina **, using 30+ years of international football results combined with historical FIFA rankings.

##  Prediction

| Team | Win Probability |
|------|-----------------|
| Argentina | **63.8%** |
| Spain | 36.2% |

*Confirmed via a 10,000-run Monte Carlo simulation.*



##  What this project does

- Merges 49,000+ historical match results with historical FIFA world rankings using `merge_asof`
- Engineers predictive features: FIFA rank/points difference, rolling recent form (last 5 matches), and head-to-head win rate
- Trains and compares three models: Logistic Regression, Random Forest, and XGBoost
- Simulates the final 10,000 times via Monte Carlo to validate the prediction
- Estimates the most likely scorelines using a Poisson goal model
- Visualizes results with custom matplotlib charts

##  Tech stack

- **Python**: pandas, numpy, scikit-learn, XGBoost, matplotlib
- **Data**: [International football results 1872-2024 (Kaggle)](https://www.kaggle.com/datasets/martj42/international-football-results-from-1872-to-2017), [FIFA World Ranking (Kaggle)](https://www.kaggle.com/datasets/cashncarry/fifaworldranking)

##  Project structure

```
worldcup-final-predictor/
├── data/raw/              # Raw CSV datasets (results + FIFA rankings)
├── notebooks/
│   └── worldcup-final-predictor.ipynb   # Full analysis pipeline
├── outputs/                # Generated charts
└── README.md
```

##  Model performance

| Model | Accuracy | Log Loss |
|-------|----------|----------|
| Logistic Regression | 70.7% | 0.557 |
| Random Forest | 70.5% | 0.564 |
| **XGBoost** | **70.9%** | **0.560** |

All three models plateau around 70% accuracy , this ceiling reflects the limits of the chosen features (FIFA ranking, recent form, head-to-head), not the choice of algorithm. Published football-prediction research typically lands in the 65-75% range, since football's outcome is inherently hard to predict , which is part of what makes it fun to watch.

##  Known limitations

- The results dataset was frozen before the 2026 semi-finals concluded, so Spain's post-semi-final FIFA ranking had to be manually substituted with its real, verified value rather than a stale one from the dataset.
- The head-to-head feature is sparse for many team pairs (few or no historical meetings), which limits its impact.
- The Poisson-based scoreline simulation models regulation-time goals independently and does not account for extra time or penalty shootouts — meaning it can't represent a "final" result for a knockout match that ends level.
- Built for portfolio/educational purposes — football remains beautifully unpredictable, and no model captures that 100%.

##  Running it yourself

```bash
python -m venv venv
venv\Scripts\activate  # or source venv/bin/activate on Mac/Linux
pip install pandas numpy scikit-learn xgboost matplotlib jupyter
```

Then open `notebooks/worldcup_final_predictor.ipynb` and run all cells.

---

*Built as a personal data science portfolio project, July 2026.*
