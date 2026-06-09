# MLB Hitter Value: Traditional Stats vs Statcast Metrics

**Are traditional hitting stats enough to explain offensive value, or do Statcast/contact-quality metrics provide stronger insight into hitter performance?**

A data science portfolio project analyzing 2025 MLB hitter performance using Baseball Savant data. The project compares traditional batting statistics against Statcast contact-quality metrics to determine which better explains and predicts offensive value, measured by wOBA.

---

## Overview

Baseball has been statistically rich for over a century, but the introduction of Statcast in 2015 added a new layer of metrics that measure how well a ball was hit, not just the outcome. This project investigates whether those newer metrics — exit velocity, launch angle, barrel rate, and others — outperform traditional stats like OPS, batting average, and OBP when it comes to explaining a hitter's offensive value.

The target variable throughout this analysis is wOBA (weighted on-base average), a well-established measure of overall offensive production.

---

## Project Structure

```
├── mlb-hitter-value-statcast.ipynb   # Main analysis notebook
├── requirements.txt                  # Python dependencies
├── data/
│   └── raw/
│       └── mlb_hitter_savant_2025_raw.csv
└── README.md
```

---

## Notebook Structure

| Section | Description |
|---|---|
| 0. Setup | Imports, constants, data loading |
| 1. Introduction | Motivation and research question |
| 2. Dataset Description | Feature categories and definitions |
| 3. Cleaning | Column standardization, name formatting, validation |
| 4. Analysis | 9 charts exploring distributions, correlations, and player comparisons |
| 5. Modeling | Linear regression with cross-validation and coefficient analysis |
| 6. Limitations | Single-season scope, sample size, multicollinearity |
| 7. Conclusion | Findings and answer to the research question |

---

## Data

Data was sourced from **[Baseball Savant](https://baseballsavant.mlb.com/leaderboard/custom)** for the 2025 MLB season.

**Filters applied:**
- Season: 2025
- Minimum plate appearances: 200

**Feature categories used:**

Traditional stats: batting average, OBP, SLG, OPS, home runs, strikeout %, walk %

Statcast/contact-quality stats: xBA, xSLG, xwOBA, average exit velocity, launch angle, barrel %, hard-hit %

To reproduce this project, download the custom leaderboard CSV from Baseball Savant with the columns used in the notebook and place it at `data/raw/mlb_hitter_savant_2025_raw.csv`, or update `csv_path` in the Setup section to point to your file.

---

## Key Findings

- Traditional stats (OPS, SLG, OBP) correlate more strongly with wOBA than Statcast metrics alone, which is expected since both measure actual outcomes.
- A linear model using only traditional features achieved an R² of ~0.996, while Statcast metrics alone reached ~0.63.
- The combined model edged out traditional stats slightly in both R² and RMSE, suggesting Statcast metrics do add information — but not as a standalone replacement.
- Players with the largest gaps between wOBA and xwOBA reveal who outperformed or underperformed their underlying contact quality in 2025.

**Conclusion:** Traditional stats are surprisingly sufficient to predict offensive value on their own. Statcast metrics are most useful as a complement — they add context that outcomes alone can't capture.

---

## Installation

Clone the repository and install dependencies:

```bash
git clone https://github.com/cgiuffrida28/mlb-hitter-value-statcast.git
cd baseball-statcast
pip install -r requirements.txt
```

Then open the notebook:

```bash
jupyter notebook mlb-hitter-value-statcast.ipynb
```

> **Note:** This notebook was developed in Google Colab. The Setup section includes a Google Drive mount — if running locally, replace the `csv_path` with your local file path and remove the Drive mount cell.

---

## Requirements

See `requirements.txt` for the full list. Core dependencies:

- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn

---

## Author

**Cole Giuffrida** — Summer 2026 Portfolio Project
