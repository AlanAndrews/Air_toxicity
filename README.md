# Incidence of respiratory diseases
**Adriana Ramírez Flores**
**Alan Andrews**
**Trang Khong**
​
---
### Problem statement
​
For this project we are participating in the Air Toxicity Kaggle Competition. 
​
We have developed several models that can accurately predict the incidence of chronic respiratory diseases based on various air toxicity parameters.
​
We hope that this analysis will be useful to epidemiologists in:
 1) determining environmental settings that trigger respiratory diseases 
 2) estimating resources necessary to treat patients suffering from respiratory diseases.
​
​
---
### Table of contents
​
- Main branch
    - ReadMe
    - Datasets
​
- A folder for each team member. Each folder includes Imputing methods and Modeling.
​
​
---
### Data analyzed
​
The data consists of several files, listed below:
- train.csv - consisting of incidence rates of respiratory disease in each state, by year, by age bracket.
- test.csv - same as train without the incidence rates.
- 4 supplemental parquet files containing 167 parameters pertaining to the following air pollutants:
    - Lead (Pb)  
    - Hazardous Air Pollutants (HAPs) 
    - Various Nitrogen Oxide compounds (NOs)
    - Volatile organic compounds (VOCs)
​
​
---
### Steps followed
​
- Data preprocessing
    - Columns with more than 20% missing data were eliminated from the parquet files
    - The data was aggregated by year and state.
    - Lag columns were created for 2, 5, and 8 years before the date in each row to take into consideration latent effects of pollutants on respiratory disease incidence rates.
    - Data from the parquet files was combined with the training and testing datasets by state/year.
​
- Exploration of different imputation methods for the missing values
    - Mean
    - Zero
    - Iterative imputation with Linear Regression
    - Iterative imputation with BayesianRidge
    - Knn imputer
​
- Exploration of different models to find the best model for the prediction
    - Linear Regression
    - Linear Regression with Lasso regularization
    - Random Forest Regressor
    - ExtraTrees Regressor
    - AdaBoost Regressor
    - Bagging Regressor
    - Neural Networks 
    - Gradient Boosting
​
- Metrics for determining the best model were R squared and Root Mean Squared Error
    - We selected these metrics because R^2 is useful because it states how much of the variation of Y is explained by the models, and RMSE is useful to have a measure in units of Y of how far in average our predictions are from the observed values.
​
The results achieved were:
![Alt text](image.png)
---
### Conclusion
​
- Model complexity does not equate to better performance.
- The method used for data imputing has an important effect on model training and performance. 
- The ‘best’ performing model in this case was RandomForestRegressor with mean imputed values in the training dataset.
- The minimum of the monthly arithmetic mean for the year of concentration of Lead (PM 2.5 LC) and Nitric Oxide (NO) are the most important pollutants when predicting the occurrence of respiratory diseases.
​
​
---
### Software requirements
​
Python libraries:
- Pandas
- Numpy
- Seaborn
- Matplotlib
- Sklearn
​
Google Collab
- Tensorflow keras
​
---