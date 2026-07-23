# Sydney Airbnb Nightly Price Prediction

## Project Overview

This project predicts the expected nightly price of an Airbnb stay in Sydney using a user's booking requirements and listing characteristics.

The analysis includes data cleaning, exploratory data analysis, feature engineering, preprocessing, model comparison, hyperparameter tuning, evaluation, residual analysis, and permutation feature importance.

## Project Objective

Build a regression model that estimates the nightly price of a Sydney Airbnb listing using features such as:

- Stay length
- Room and property type
- Accommodation capacity
- Bedrooms and bathrooms
- Location
- Host and review information
- Amenities

## Workflow

1. Cleaned the raw Airbnb listing data.
2. Created nightly price as the prediction target.
3. Split the data into training and test sets.
4. Explored price distributions and feature relationships.
5. Engineered booking and listing features.
6. Built preprocessing pipelines for numerical and categorical data.
7. Compared linear, ensemble, and baseline regression models using five-fold cross-validation.
8. Selected and tuned XGBoost.
9. Evaluated the final model on unseen test data.
10. Examined prediction errors and permutation feature importance.

## Models Compared

- Dummy Regressor
- Linear Regression
- Ridge Regression
- Random Forest
- Gradient Boosting
- XGBoost

XGBoost was selected because it achieved the strongest cross-validation performance. Tree-based models also performed better than linear models, suggesting that Airbnb prices contain nonlinear relationships and feature interactions.

## Best XGBoost Parameters

- **Number of trees:** 1,000
- **Maximum tree depth:** 5
- **Learning rate:** 0.1

After tuning, the cross-validated RMSLE improved from **0.353 to 0.337**.

## Test Results

### Original AUD price scale

- **MAE:** \$141.74 per night
- **RMSE:** \$1,233.71 per night
- **R²:** 0.158

### Log-price scale

- **MAE:** 0.226
- **RMSLE:** 0.360
- **R²:** 0.845

The model captures typical and proportional pricing patterns well. However, a small number of extremely expensive listings substantially increase the error measured on the original price scale.

## Most Important Predictors

Permutation importance identified the following influential predictors:

1. Stay length
2. Room type
3. Accommodation capacity
4. Longitude
5. Number of bedrooms
6. Latitude

These findings indicate that booking duration, property size, room type, and location are important factors in nightly pricing.

## Limitations

- The model is less reliable for extremely high-priced listings.
- The 15 largest prediction errors account for **97.1% of the total squared error**.
- The raw-price RMSE and R² are strongly affected by these extreme observations.
- Predictions should be treated as estimates rather than guaranteed market prices.

## Repository Structure

```text
.
├── Airbnb.ipynb
├── README.md
└── dataset/
    └── 2026listings.csv
```

## Tools and Libraries

- Python
- pandas
- NumPy
- Matplotlib
- Seaborn
- scikit-learn
- XGBoost
- Jupyter Notebook

## How to Run

1. Clone or download this repository.
2. Place `2026listings.csv` inside the `dataset` folder.
3. Install the required Python libraries.
4. Open `Airbnb.ipynb` in Jupyter Notebook or JupyterLab.
5. Run the notebook from top to bottom.

## Conclusion

The final XGBoost model provides useful nightly-price estimates for typical Airbnb listings in Sydney. Its predictions are strongest for common listings, while estimates for unusually expensive properties should be interpreted with caution.
