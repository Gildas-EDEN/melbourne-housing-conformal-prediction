# Melbourne Housing Conformal Prediction

## Project Overview

This project investigates Melbourne house price prediction and the use of conformal prediction intervals to quantify uncertainty. It compares two regression models, Linear Regression and Random Forest, and evaluates two conformal procedures: Jackknife and five-fold cross-validation.

The analysis considers both point prediction accuracy and interval quality, measured through empirical coverage and mean interval width. Coverage is also examined across property types.

## Dataset

The project uses the [Melbourne Housing Market dataset on Kaggle](https://www.kaggle.com/datasets/anthonypino/melbourne-housing-market).

The original dataset contains 34,857 transactions and 21 variables. It includes sale prices and property characteristics such as the number of rooms, property type, distance, land size, building area, year built, and location.

The target variable is `Price`, a continuous house sale price. The predictors used include property characteristics, geographical coordinates, property type, and region. The target is transformed using the natural logarithm for modelling.

After preprocessing, the analysis uses 27,244 transactions and 21 variables.

## Project Workflow

1. **Explore missing data:** Visualize missingness patterns and examine nullity correlations and a dendrogram using `missingno`.
2. **Preprocess the data:** Remove rows without a target price, remove a duplicate, impute missing predictor values, and treat outliers using the interquartile range rule.
3. **Prepare model inputs:** Encode categorical predictors, standardize numerical predictors where required, and split the data into training and test sets.
4. **Train regression models:** Compare Linear Regression with Random Forest.
5. **Construct prediction intervals:** Evaluate Jackknife and five-fold cross-validation conformal procedures.
6. **Assess results:** Compare regression metrics, interval coverage, mean width, and coverage across property types.

## Models and Evaluation

The models are evaluated using RMSE, MAE, and \(R^2\), calculated on the log-price scale. Conformal intervals are compared using empirical coverage and mean interval width.

At a nominal coverage level of 90%, the results are:

| Model | Conformal procedure | Empirical coverage | Mean interval width (log scale) |
|---|---|---:|---:|
| Linear Regression | Jackknife | 90.2% | 0.819 |
| Linear Regression | Five-fold cross-validation | 90.3% | 0.825 |
| Random Forest | Jackknife | 91.4% | 0.664 |
| Random Forest | Five-fold cross-validation | 91.9% | 0.679 |

For point prediction, the Random Forest model used in the conformal evaluation achieves an \(R^2\) of 0.901, an RMSE of 0.164, and an MAE of 0.118. Linear Regression achieves an \(R^2\) of 0.764, an RMSE of 0.253, and an MAE of 0.192.

Random Forest produces narrower intervals than Linear Regression in the reported comparisons. The highest empirical coverage at the 90% nominal level is obtained with Random Forest and five-fold cross-validation.

## Property-Type Analysis

Coverage is not identical across property types. At the 90% nominal level, coverage for type `u` is below 90% for both conformal procedures when using Random Forest. This subgroup analysis complements the overall coverage results.

## Skills Demonstrated

- Data cleaning and preprocessing
- Missing-data exploration with `missingno`
- Numerical imputation using an iterative imputer and `ExtraTreesRegressor`
- Outlier detection and treatment using the interquartile range rule
- Categorical encoding and numerical standardization
- Regression modelling with Linear Regression and Random Forest
- Conformal prediction and prediction-interval evaluation
- Model assessment using RMSE, MAE, \(R^2\), empirical coverage, and mean interval width
- Subgroup analysis by property type

## How to Run

1. Open the `.ipynb` notebook included in this repository using Jupyter Notebook, JupyterLab, or Google Colab.
2. Run the notebook cells in order, from data loading and preprocessing through model evaluation.
3. Use the Kaggle dataset linked above as the data source.

The notebook contains the data-processing, modelling, and evaluation workflow for the project.
