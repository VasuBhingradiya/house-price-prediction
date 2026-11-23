# House Price Prediction — Advanced (PRCP-1020)

Predicting house sale prices on the Kaggle **House Prices: Advanced Regression
Techniques** dataset (Ames Housing, 1,460 homes sold 2006–2010, target `SalePrice`).

## Results (80/20 split, seed 42, target log1p(SalePrice))

| Model | Test RMSE ($) | R² |
|---|---:|---:|
| Baseline (predict the mean) | 88,271 | — |
| Ridge Regression (alpha = 10) — **final pick** | **25,107** | **0.9002** |
| HistGradientBoosting | 29,080 | 0.8974 |
| Random Forest (300 trees) | 29,740 | 0.8863 |

HistGradientBoosting had the best 5-fold CV RMSE(log) (0.1338) but was worse on
the test set, so **Ridge** is the production pick. Top price drivers:
OverallQual, GrLivArea, TotalBsmtSF. No hyperparameter tuning was done
(exam week) — stated honestly in the notebook's Challenges section.

## Layout

```
house-price-prediction/
├── README.md
├── requirements.txt
├── data/
│   └── data.csv                      # Kaggle train file (1,460 × 81)
├── notebooks/
│   └── HousePrice_PRCP1020.ipynb     # executed final notebook (Tasks 1–3,
│                                     # Model Comparison, Challenges)
├── models/
│   └── houseprice_final_model.pkl    # Ridge (alpha = 10), trained on log price
└── reports/
    ├── houseprice_final_comparison.csv
    └── houseprice_missing_summary.csv
```

## Run it

```bash
pip install -r requirements.txt
jupyter notebook notebooks/HousePrice_PRCP1020.ipynb   # Kernel → Restart & Run All
```

## Data source

Kaggle House Prices: Advanced Regression Techniques
(https://www.kaggle.com/c/house-prices-advanced-regression-techniques/data).
Statement file: `house_prices.docx` (PRCP-1020).
