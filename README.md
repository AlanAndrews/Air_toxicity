# !PROJECT IN PROGRESS!

# Air_toxicity
GitHub repository for Air Toxicity and Chronic Respiratory Diseases Kaggle competition. Also being used to satisfy requirements for General Assembly project 5.


Air Toxicity Kaggle Competition
https://www.kaggle.com/competitions/air-toxicity-and-chronic-respiratory-diseases-us/data

Training and Test Data
The training dataset has 5 columns and 4500 rows.

| ID         | Stat.Name  | Year | Age         | Incidence     | 
|------------|------------|------|-------------|---------------|
|f8312a4|Alabama|1990|65-69|4685.28431349409|
|3effa36|Alabama|1990|70-74|4827.05204294459|
|1e8044b|Alabama|1990|75-79|4377.95691363824|
|d875d65|Alabama|1990|80-84|3822.73299310537|


The data is for 1990 to 2019. There are 6 age categories.

The test dataset has the same columns but is missing the Incidence of respiratory diseases. That is what we will be predicting.


Supplemental Data Files
There are 4 parquet files pertaining to different air pollutants: 
Lead (Pb),  Hazardous Air Pollutants (HAPs), various Nitrogen Oxide compounds (NOs), and volatile organic compounds. (VOCs).

Each parquet file is composed of a different subset of analytes:

Parquet File
Number of Analytes
Pb
3
HAPs
41
NOs
3
VOCs
120


The data in the parquet files is organized by the state the sample was taken and the date YYYY-MM-DD format. We will need to aggregate the data








Notes Parameters.
Lead (TSP) STP → Total Suspended Particulate - Standard Temperature Pressure


What to do:
What to do with data older than 1990? Our training data goes from 1990 to 2019. The data in the parquet files goes back to 1980. Adriana suggested creating lag variables. That is, creating columns for each parameter per year 

Many missing values. There are many missing values in the resultant dataframe from merging the training dataset with the parquet files. How do we handle missing values.
Dropping. Not ideal from an analysis perspective. We would lose a lot of data. T
Inserting the average value for all nulls.
Imputation. Many techniques we could implement. General categories are Univariate and Multivariate imputation. 



References:
Methods for imputation of missing values in air quality data sets
https://www.sciencedirect.com/science/article/pii/S1352231004001815
In they evaluated various imputation methods applicable to air quality data sets including: “univariate (linear, spline and nearest neighbor interpolation), multivariate (regression-based imputation (REGEM), nearest neighbor (NN), self-organizing map (SOM), multi-layer perceptron (MLP)), and hybrid methods” on simulated data patterns
Univariate nearest neighbor imputation is probably the simplest scheme available, in that the endpoints of the gaps are used as estimates for all the missing values (Nearest neighbor, linear and cubic spline interpolation)
Various Multivariate imputation methods. 


Scikit-Learn documentation
https://scikit-learn.org/stable/modules/impute.html
Univariate vs. Multivariate imputation
i.e. simple and easy vs sophisticated and more complicated.
Marking imputed values. Transformer for adding a binary column to mark imputed vs non-imputed. 
Various estimators that can handle NaN https://scikit-learn.org/stable/modules/impute.html#estimators-that-handle-nan-values




Data that could be added to the analysis:
Meteorological data
