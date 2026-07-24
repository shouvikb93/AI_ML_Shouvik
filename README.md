# Week 1 Assignment — Statistics & Regression on California Housing

## Project Overview
An end-to-end statistical analysis and linear regression study on the
California Housing dataset (20,640 census block groups). The project covers
data import and inspection, data cleaning, exploratory data analysis (EDA),
simple and multiple linear regression, a visualization portfolio, and a
written reflection.

## How to Run
1. Install dependencies:
   `pip install -r requirements.txt`
2. Ensure the dataset `housing.csv` is available. The notebook loads it with
   `pd.read_csv("housing.csv")`, so keep a copy of `housing.csv` in the same
   folder as the notebook (a copy is also provided in `data/`).
3. Open `Week1_Statistics_Regression.ipynb` in Jupyter Notebook or VS Code.
4. Run all cells top to bottom (Kernel -> Restart & Run All).

## Libraries Required
pandas, numpy, matplotlib, seaborn, scikit-learn, jupyter
(see requirements.txt for versions)

## Dataset
California Housing dataset — each row is a census block group, not a single
house. Target variable: median_house_value. Nine numerical features and one
categorical feature (ocean_proximity).

## Key Findings
1. median_income is the strongest predictor of house value (r = 0.69).
2. The target (median_house_value) is artificially capped at $500,001 due to
   top-coding in the 1990 US Census. This appears as a spike in the histogram
   and a diagonal band in the residual plot, and it limits achievable accuracy.
3. The four size features (total_rooms, total_bedrooms, population, households)
   are severely multicollinear (r = 0.86–0.97), so engineered per-household
   ratio features were used instead of the raw totals.
4. Simple linear regression on median_income alone achieved R² = 0.46.
5. Multiple linear regression (5 features) improved this to R² = 0.52 — but
   only after clipping extreme outliers in the engineered ratio features; an
   initial attempt scored worse (R² = 0.41) due to those outliers.
6. Adding location features (latitude, longitude, one-hot ocean_proximity)
   further improved the model to R² = 0.63 while keeping it purely linear.
7. Location coordinates were weak predictors individually but strong jointly,
   showing that correlation (measured one feature at a time) can understate a
   feature's value in a multi-feature model.
