# Car Price Prediction Using Regression

## Overview
This project is part of the MIT Applied Data Science Program. It focuses on predicting the price of used cars using various regression techniques. The goal is to help companies like Cars4U make informed pricing decisions based on car features such as brand, age, mileage, and power.

## Problem Statement
The used car market is a USD 32.14 billion industry with complex factors driving pricing. Predicting used car prices is challenging due to the subjective factors like scarcity and consumer preferences, alongside objective factors like car age and mileage.

## Dataset
The dataset is divided into three main categories:
1. **Supply and Demand Factors**: Brand, location.
2. **Car Characteristics**: Power, mileage, transmission type, seating capacity.
3. **Condition and Care**: Kilometers driven, age, number of previous owners.

The dataset required significant cleaning and feature engineering to handle skewed distributions, outliers, and missing values. We removed the 'new price' variable due to over 85% missing values, as filling these could introduce noise.

## Methodology
### Data Preprocessing:
- **Outliers and Skewness**: Addressed by capping kilometers driven at the 95th percentile and applying logarithmic transformation.
- **Feature Engineering**: 
   - Target encoding was used for the `Brand` feature.
   - `Kilometers driven` was binned into intervals of 20,000 km.
   - Scaled the features to manage varying ranges of values.

### Models Used:
- **Linear Regression**
- **Ridge/Lasso Regression**
- **Decision Tree**
- **Random Forest**

### Key Findings:
- **Random Forest** provided the best performance with the lowest errors (MAE, RMSE) and the highest R² scores. It handled non-linear relationships between the features and target price effectively and was less prone to overfitting compared to Decision Trees.
- The model tends to underestimate prices of high-end cars due to subjective factors such as scarcity and market trends, which are difficult to quantify.

## Results
### Model Performance:
| Model               | MAE Train | MAE Test | RMSE Train | RMSE Test | R² Train | R² Test |
|---------------------|-----------|----------|------------|-----------|----------|---------|
| Linear Regression    | 0.167     | 0.163    | 0.226      | 0.219     | 0.909    | 0.915   |
| Decision Tree        | 0.004     | 0.152    | 0.017      | 0.216     | 1.000    | 0.917   |
| Random Forest        | 0.045     | 0.116    | 0.066      | 0.166     | 0.992    | 0.951   |
| Lasso                | 0.167     | 0.163    | 0.226      | 0.219     | 0.909    | 0.915   |

### Important Features:
- **Power**: 61.1%
- **Age (Year)**: 20.7%
- **Brand**: 8.0%
- **Engine**: 4.8%
- **Mileage**: 1.5%
- Other features like seats and location contributed less than 1% each.

## Business Recommendations
- **Market Segmentation**: The model performs well for lower-priced cars but underestimates high-end cars. We recommend building separate models for luxury and non-luxury cars to address the varying price influences in each segment.
- **Feature Insights**: Cars4U can prioritize acquiring cars with high power, recent models, and strong brands to improve profitability. Additionally, understanding which features most impact price can help guide inventory management and marketing strategies.

## Tools and Libraries Used
- **pandas**: For data manipulation and handling missing values.
- **numpy**: For numerical operations.
- **matplotlib** and **seaborn**: For data visualization.
- **scikit-learn**: For model building and evaluation.
- **category_encoders**: For target encoding the `Brand` feature.
- **eli5**: For feature importance analysis in the Random Forest model.
- **Shap**: For interpreting Random Forest model predictions.

## How to Run the Project
1. Clone the repository:
   ```bash
   git clone https://github.com/knzymx/portfolio