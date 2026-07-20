# Medical Insurance Cost Prediction using Multiple Linear Regression

**Assignment 1 – AI/ML**

## Objective

To develop a Multiple Linear Regression model that predicts an individual's
medical insurance `charges` based on personal and health-related attributes
(age, sex, BMI, number of children, smoking status, and region), and to
evaluate the model's performance.

## Dataset Link

**Medical Cost Personal Insurance Dataset (Kaggle)**
https://www.kaggle.com/datasets/mirichoi0218/insurance

> Note: The dataset is **not** included in this repository. Please download
> `insurance.csv` from the Kaggle link above and place it in the project root
> before running the notebook/script.

## Libraries Used

- `pandas` – data loading and manipulation
- `numpy` – numerical operations
- `matplotlib` – plotting (Actual vs Predicted scatter plot)
- `scikit-learn` – `train_test_split`, `LinearRegression`, `LabelEncoder`,
  evaluation metrics (`mean_absolute_error`, `mean_squared_error`, `r2_score`)

## Methodology

1. **Data Understanding**
   - Loaded the dataset with Pandas and inspected the first five records.
   - Identified feature types:
     - Numerical: `age`, `bmi`, `children`
     - Categorical: `sex`, `smoker`, `region`
     - Target: `charges`

2. **Data Preprocessing**
   - Checked for missing values (none found).
   - Encoded `sex` and `smoker` using Label Encoding (binary categories).
   - Encoded `region` using One-Hot Encoding (multi-class category),
     dropping the first category to avoid the dummy-variable trap.
   - Split the data into 80% training and 20% testing sets
     (`random_state=42` for reproducibility).

3. **Model Development**
   - Trained a `LinearRegression` model on all encoded features
     (age, sex, bmi, children, smoker, region) to predict `charges`.
   - Generated predictions on the held-out test set.

4. **Model Evaluation**
   - Computed MAE, MSE, RMSE, and R² on the test set.
   - Plotted Actual vs Predicted charges (see `actual_vs_predicted.png`).

## Results

| Metric | Value |
|--------|-------|
| MAE    | 4,181.19 |
| MSE    | 33,596,915.85 |
| RMSE   | 5,796.28 |
| R²     | 0.7836 |

**Model coefficients:**

| Feature | Coefficient |
|---|---|
| age | 256.98 |
| sex | -18.59 |
| bmi | 337.09 |
| children | 425.28 |
| smoker | 23,651.13 |
| region_northwest | -370.68 |
| region_southeast | -657.86 |
| region_southwest | -809.80 |
| Intercept | -11,931.22 |

**Observations:**

1. **Smoking status is the dominant driver of cost** — its coefficient (~23,651)
   dwarfs every other feature's, meaning smokers are billed dramatically higher
   charges than non-smokers, all else being equal.
2. **Age and BMI have a positive, moderate effect** on charges, matching the
   intuition that older and higher-BMI individuals tend to incur higher
   medical costs.
3. **The model explains about 78% of the variance** in charges (R² ≈ 0.78),
   but the scatter plot shows two distinct clusters (smokers vs. non-smokers)
   and larger errors at higher charge values, suggesting the true relationship
   isn't perfectly linear and that interaction effects (e.g., BMI × smoker)
   aren't captured by this simple model.

![Actual vs Predicted Charges](actual_vs_predicted.png)

## Conclusion

The Multiple Linear Regression model built on age, sex, BMI, number of
children, smoking status, and region provides a reasonable first
approximation of medical insurance charges, achieving an R² of about 0.78 on
the held-out test set. Among all predictors, **smoking status** emerges as by
far the strongest driver of cost, followed by **age** and **BMI**, while
**sex**, **number of children**, and **region** contribute comparatively
little to the prediction. These findings align with real-world expectations,
since smoking and higher BMI are well-known risk factors for chronic illness,
which insurers price into premiums. However, a key **limitation of Linear
Regression** here is its assumption of a strictly linear, additive
relationship between features and charges; in reality, factors like smoking
and BMI likely interact (e.g., a high-BMI smoker may cost disproportionately
more than the sum of their individual effects), and charges are also
right-skewed with outliers — both of which a simple linear model cannot fully
capture. More flexible models (e.g., polynomial regression, tree-based
ensembles) could likely improve predictive accuracy.

## Repository Structure

```
.
├── Assignment-1.ipynb        # Jupyter notebook (full analysis)         
├── actual_vs_predicted.png   # Actual vs Predicted scatter plot
└── README.md
```

## How to Run

```bash
pip install pandas numpy matplotlib scikit-learn
# Download insurance.csv from the Kaggle link above into this folder
python Assignment-1.py
# or open Assignment-1.ipynb in Jupyter
```
