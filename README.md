# Retail Profit Leakage & Sales Forecasting

**Business Analytics | Dynamic Pricing | Statistical Analysis | Machine Learning**

## 📌 Overview

**What if a business is generating billions in revenue while silently losing profit on every fourth transaction?**

This project combines business analytics and machine learning to investigate a critical retail pricing problem and forecast future sales performance.

Developed for a Datathon competition, the project addresses two connected challenges:

- **Part 2 | Business Problem Solving:** Diagnose profit leakage, identify its root causes, and evaluate pricing interventions.
- **Part 3 | Machine Learning:** Forecast revenue using feature engineering, time-series validation, and ensemble learning.

The central objective is to move beyond prediction and translate analytical findings into measurable business decisions.

## 🔍 Part 2: Business Problem Solving

### The Business Problem

Between 2013 and 2022, the business recorded **714,653 transaction lines** and generated **15.68 billion VND in net revenue**.

However, loss-making transactions significantly reduced profitability.

| Key Metric | Finding |
|---|---:|
| Net Revenue | 15.68B VND |
| Potential Gross Profit | 2.43B VND |
| Actual Gross Profit | 1.52B VND |
| Profit Leakage | **915.5M VND** |
| Share of Potential Profit Lost | **37.6%** |

### Root Cause Investigation

The analysis uncovered a critical weakness in the dynamic pricing mechanism: transaction prices were not consistently constrained by product costs.

**Key findings:**

- **833.8M VND** in losses originated from base selling prices below COGS, compared with **81.7M VND** attributable to discounts.
- **Streetwear and Outdoor** accounted for 93.5% of base-price losses.
- The *Urban Blowout* campaign exhibited a 99.9% loss-making transaction rate despite relatively small effective discounts.
- Statistical tests found little practical evidence that overstock clearance explained the losses.

**Core insight:** The primary issue was not excessive discounting, but an underlying pricing mechanism operating without adequate cost-based safeguards.

### Forecasting Profit Leakage

The analysis identified a recurring Q3 loss pattern, particularly in odd-numbered years when multiple campaigns overlapped.

A six-variable linear regression model was developed to forecast quarterly losses.

| Metric | Result |
|---|---:|
| R² | 0.772 |
| RMSE | 9.21M VND |
| Forecast Losses (2023–2024) | **192.1M VND** |

### Recommended Interventions

Three complementary policies were evaluated:

1. **Cost-Based Price Floor:** Enforce a minimum selling price of `COGS × 1.10`.
2. **Campaign Eligibility Control:** Validate pricing constraints before including products in promotions.
3. **Promotion Scheduling:** Limit overlapping campaigns and reschedule high-risk Q3 promotions.

| Scenario (2023–2024) | Forecast Loss | Estimated Savings |
|---|---:|---:|
| No intervention | 192.1M VND | — |
| Price floor | 31.8M VND | 160.4M VND |
| Price floor + scheduling | **6.9M VND** | **185.3M VND** |

These are model-based and simulated estimates, not realized financial savings.

## 🤖 Part 3: Machine Learning

### Forecasting Objective

Develop a robust revenue forecasting pipeline capable of capturing seasonal patterns, promotional effects, and changing business conditions.

### Modeling Approach

The solution combines feature engineering with an ensemble of tabular machine learning models.

**Pipeline:**

1. **Data Preparation:** Integrate historical sales information and construct time-based features.
2. **Feature Engineering:** Capture Tet holiday effects, month-end patterns, Fourier seasonality, and promotional activity.
3. **Model Training:** Train Ridge Regression, LightGBM, and CatBoost on transformed targets.
4. **Quarter Specialists:** Develop quarter-specific models to better capture seasonal behavior.
5. **Ensembling:** Combine complementary predictions to improve robustness.
6. **Calibration:** Adjust forecast levels using validation and public leaderboard feedback.

### Forecasting Performance

| Metric | Result |
|---|---:|
| Evaluation | Kaggle Public Leaderboard |
| Best MAE | **659,351.99** |
| Main Models | Ridge, LightGBM, CatBoost |
| Key Techniques | Ensemble Learning, Feature Engineering, Seasonal Calibration |

### Model Interpretability

Feature importance and SHAP analysis highlighted several influential factors:

- **Tet holiday proximity:** Strong changes in predicted revenue around the holiday period.
- **Month-end effects:** Recurring positive contributions near the end of each month.
- **Q4 seasonality:** Distinct year-end patterns, particularly in odd-numbered years.
- **Promotional activity:** Active campaigns contributed meaningfully to revenue predictions.

These findings support the importance of combining domain knowledge with machine learning rather than relying exclusively on generic time-series features.

## 💡 Key Takeaways

- **Revenue growth does not guarantee profitability.** Pricing constraints matter as much as sales performance.
- **Root-cause analysis changes the intervention.** Correcting the pricing mechanism is more valuable than simply reducing discounts.
- **Seasonality is both a forecasting signal and a business risk.** Campaign timing influences revenue and potential losses.
- **Prediction becomes more useful when connected to decisions.** The revenue forecasting output also supports the profit leakage forecasting framework.

## ⚖️ Strengths & Limitations

**Strengths**
- Integrates business diagnosis, statistical testing, forecasting, and policy simulation.
- Quantifies financial impact rather than relying solely on descriptive insights.
- Combines domain-driven feature engineering with ensemble machine learning.
- Uses interpretable statistical models and SHAP to support analytical conclusions.

**Limitations**
- Estimated policy savings depend on pricing and demand assumptions.
- Forecasting results may be sensitive to changing promotional strategies and market conditions.
- Public leaderboard performance does not establish generalization to unseen private test data.
- Proposed interventions require real-world experimentation before operational deployment.

## 🛠️ Tech Stack

`Python` · `Pandas` · `NumPy` · `Scikit-learn` · `LightGBM` · `CatBoost` · `SHAP` · `Statistical Testing` · `Jupyter Notebook`

## 📂 Repository Structure

```text
retail-profit-leakage-and-sales-forecasting/
├── Part 2 Code/          # Business problem solving: profit leakage analysis, pricing diagnosis, statistical tests, and policy simulation
├── Part 3 Code/          # Machine learning: feature engineering, revenue forecasting, ensemble modeling, and model interpretation
├── Datathon_Report.pdf  # Full analytical report covering both competition tasks
└── README.md
```

## 🎓 Project Context

- **Project Type:** Datathon Competition
- **Team:** LOVISONG
- **Focus:** Business Problem Solving & Machine Learning
- **Deliverables:** Business investigation, predictive models, policy recommendations, and technical report

*The most interesting problems are not always about building a better model. Sometimes, the real challenge is asking the right question, uncovering what the numbers are hiding, and turning evidence into decisions that matter.*
