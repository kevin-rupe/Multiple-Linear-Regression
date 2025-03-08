# Multiple-Linear-Regression
Project completed in pursuit of Master's of Science in Data Analytics.

## RESEARCH QUESTION 

The medical dataset for this assessment includes a lot of patient information from demographic information, medical history, and even financial information. I would like to determine which variables correlate to the total charges the customer received. For that reason, my research question is, “What variables are highly correlated to the total amount the patient is charged?”

## GOALS OF ANALYSIS

My goals for this performance assessment are simply stated: I want to gain more insight into what statistical medical, geographical, or personal data have correlation to the total amount the patient was charged for their stay in the hospital.

## SUMMARY OF ASSUMPTIONS

Four assumptions of multiple linear regression models are as summarized first by stating that there must not be any collinearity between the independent variables chosen in your model. This is better stated that the independent variables cannot be too highly correlated with each other. Second, we assume that there is a linear relationship between the dependent and independent variables. Third, observations in our model should be selected at random as well as independent of the population. And lastly, the residuals should be normally distributed where the overall residual mean is zero (CFA Institute, 2024).

## TOOL BENEFITS

There are many benefits to using Python for data analysis. There are so many libraries that can be loaded that make analysis much easier than attempting to manually analyze the data. First, libraries such as Pandas, NumPy and Matplotlib allow for easy manipulation of data using statistics, data frames, and visualization (Pandas, 2023). Second, the statsmodels libraries perform many complicated regression techniques with just a few simple lines of code. So long as the analyst interprets the results correctly, you can rest assured that these libraries will give the most accurate results (Perktold, J., 2009-2023). 

## APPROPRIATE TECHNIQUE

Multiple Linear Regression is an appropriate technique to analyze how certain variables in the dataset are correlated. Using Python libraries such as statsmodels can help you determine how closely the dependent variable is correlated to multiple explanatory variables. Using the Seaborn and Matplotlib libraries gives you a visual representation of how closely the variables are linearly related. Multiple Linear Regression allows the analyst to predict with some certainty what level of effect the explanatory variables have on the dependent variable (Massaron, L., 2016). 

## DATA CLEANING

Before I can start multiple linear regression, I need to ensure the dataset is clean. To start, I will clean the data by finding any duplicate values using the duplicated( ) method which checks across rows for duplicates. I will treat any duplicate rows by dropping them from the dataset using the drop_duplicates Pandas command. I will also look for missing values using the isnull( ) and isna( ) functions. If any are found, I will treat these values by dropping them or using statistical imputation to impute the values. I will also treat outliers in the same way I treat missing values. Lastly, though not considered ‘data cleaning,’ I will wrangle categorical variables using re-expression techniques such as one-hot-encoding or Pandas’ dummy variables. 

Below is the annotated code that I used to clean the data.

```python
#find duplicates
print(med_data.duplicated().value_counts())
print(med_data.duplicated('Customer_id', keep=False).value_counts()) print(med_data.duplicated('Interaction', keep=False).value_counts()) 
print(med_data.duplicated('UID', keep=False).value_counts())

#find missing values using msno matrix
msno.matrix(med_data, labels=True)

#find total number of missing values
med_data_nullity = med_data[['Children', 'Age', 'Income', 'Soft_drink', 'Overweight', 'Anxiety', 'Initial_days']].isnull()
print(med_data_nullity.sum())
```

## SUMMARY STATISTICS 

**Dependent Variable: TotalCharge**

![IMG_1588](https://github.com/user-attachments/assets/45349914-f8db-4e13-8f4d-e2f6a29ac336)

The average value in TotalCharge is around $5,312. The range of all values is from $1,938 to $9,180. The standard deviation is $2,180 which means that around two-thirds of all values are +/- that amount from the average value (i.e., “mean”). 95% of all values lie within two standard deviations from the mean (i.e., range of +/- $4,360 from $5,312). The TotalCharge variable is bimodally distributed. 


**Continuous Independent Variable: Initial_days**

![IMG_1589](https://github.com/user-attachments/assets/97179200-2f81-4e89-8e94-819615e5160c)

The average value in Initial_days is around 34 ½ days. The range of all values is from 1 day to 72 days. The standard deviation is 26 days which means that around two-thirds of all values are +/- that amount from the average value (i.e., “mean”). 95% of all values lie within two standard deviations from the mean (i.e., range of +/- 52 from 34 ½ days). The Initial_days variable is bimodally distributed. 

**Categorical Independent Variables**

These independent variables are categorical and therefore do not give the same statistical data as the continuous variables above do. Provided below are screenshots of how each of these variables is distributed. Each variable contains 10,000 observations. 

![IMG_1590](https://github.com/user-attachments/assets/1c5ca799-13ee-4e6e-9d56-9c8a3e4eda18)
          
## VISUALIZATIONS

![IMG_1591](https://github.com/user-attachments/assets/e78287df-3632-4456-a0fa-a7321c77692f)
![IMG_1592](https://github.com/user-attachments/assets/b134eb8b-a39c-4828-aab0-cf4d4acba297)
![IMG_1593](https://github.com/user-attachments/assets/6f925a75-be0b-4d27-ae56-cac754381c79)
![IMG_1594](https://github.com/user-attachments/assets/7932a94a-fc07-464c-9e73-699be360475e)
![IMG_1595](https://github.com/user-attachments/assets/ec165c27-d590-474c-b808-a50f6c7d647b)
![IMG_1596](https://github.com/user-attachments/assets/1e2547f3-9dd2-4900-8e7f-8aefa5e58ee8)
![IMG_1597](https://github.com/user-attachments/assets/715a4267-435d-4236-af98-662b20ff3e4d)
![IMG_1598](https://github.com/user-attachments/assets/fd4dacc0-fd0c-47c0-a1dc-fff35433255a)
![IMG_1603](https://github.com/user-attachments/assets/dab30de2-1d0f-43d0-9119-da26db7322b9)
![IMG_1602](https://github.com/user-attachments/assets/d80144fe-2024-443a-addb-5ad7c214d865)
![IMG_1601](https://github.com/user-attachments/assets/45f67039-724e-4b68-b9bd-5d0e863cbeba)
![IMG_1600](https://github.com/user-attachments/assets/af0406f1-fb45-47be-8ad9-c642eb92184f)
![IMG_1599](https://github.com/user-attachments/assets/0b1235fe-64bf-4022-b0dc-46f116a10531)
![IMG_1608](https://github.com/user-attachments/assets/9eed768c-3ba7-4488-9834-d50d57d9d38d)
![IMG_1607](https://github.com/user-attachments/assets/95eb93c1-035a-4fb2-9970-9cd2c38264dd)
![IMG_1606](https://github.com/user-attachments/assets/1915b546-7acd-4ec8-b5ef-0e72bf04fc8e)
![IMG_1605](https://github.com/user-attachments/assets/4d2ca9c0-db1a-4d74-a5d9-225152e3b72b)
![IMG_1604](https://github.com/user-attachments/assets/63d754eb-7291-4c1b-99e9-4e8751cb74b8)
![IMG_1611](https://github.com/user-attachments/assets/4acac3af-dd98-484a-840f-9201a4de463b)
![IMG_1610](https://github.com/user-attachments/assets/92170d56-a0a8-4669-993a-fc7beb51004c)
![IMG_1609](https://github.com/user-attachments/assets/db37bf52-2841-4fbb-b3e7-0988bbb9c2da)


## DATA TRANSFORMATION

I chose several categorical variables and as such had to perform re-expression of these variables so they could be used in the predictive modeling. I created dummy variables on all the “yes/no” variables and Area, Initial_admin, and Services. I used Ordinal Encoding on Complication_risk. The annotated code for these steps is below.

```python
prefix_list = ['ReAdmis', 'HighBlood', 'Diabetes', 'Hyperlipidemia', 
               'Allergic_rhinitis', 'Reflux_esophagitis']

med_data = pd.get_dummies(med_data, 
                          prefix=prefix_list, 
                          prefix_sep='_', 
                          dummy_na=False,
                          drop_first=True,
                          columns=prefix_list)

med_data['Comp_risk_numeric'] = med_data['Complication_risk']
dict_comp_risk =  {"Comp_risk_numeric": {"Low": 1, "Medium": 2, "High": 3}}
med_data.replace(dict_comp_risk, inplace=True)

dummies_area = pd.get_dummies(med_data.Area)
dummies_admin = pd.get_dummies(med_data.Initial_admin)
dummies_svc = pd.get_dummies(med_data.Services)

original_df = med_data
med_data = pd.concat([med_data, 
                      dummies_area, 
                      dummies_admin,
                      dummies_svc], axis='columns')

```


## INITIAL MODEL

![Image 3-8-25 at 9 30 AM](https://github.com/user-attachments/assets/de4497da-e6b0-46d9-9719-9759e88ecbe6)

## JUSTIFICATION OF MODEL REDUCTION

Before reducing the model, I checked the variables for multicollinearity using statsmodels variance_inflation_factor (VIF) package. I removed variables one-by-one, re-running VIF each time to re-check for multicollinearity. I removed Additional_charges, Doc_visits, and VitD_levels, which all had values larger than 10.

```python
## Checking for Multicollinearity

# Import functions
from statsmodels.stats.outliers_influence import variance_inflation_factor

# Get variables for which to compute VIF and add intercept term
X = med_data[['Income', 'Children', 'Age', 'Full_meals_eaten', 'VitD_supp', 'Initial_days', 
              'Comp_risk_numeric', 'ReAdmis_Yes', 'HighBlood_Yes', 'Diabetes_Yes', 
              'Hyperlipidemia_Yes', 'Allergic_rhinitis_Yes', 'Reflux_esophagitis_Yes']]

# Compute and view VIF
vif = pd.DataFrame()
vif["variables"] = X.columns
vif["VIF"] = [variance_inflation_factor(X.values, i) for i in range(X.shape[1])]

# View results using print
print(vif)
```
![Image 3-8-25 at 9 32 AM](https://github.com/user-attachments/assets/16869e48-fa96-4592-929e-a8ad275e3265)

To reduce the model, I used the backward stepwise elimination wrapper method of feature selection. Looking at the p-values in the regression summary table, I removed the largest p-value variable one at a time until no p-values were left that were larger than 0.05. P-values that are larger than 0.05 are statistically insignificant and should not be included in our model. This method removed Income, Children, Age, Full_meals_eaten, and VitD_supp.


## REDUCED LINEAR REGRESSION MODEL

![Image 3-8-25 at 9 34 AM](https://github.com/user-attachments/assets/2fbf3a3c-f749-4a89-960b-60a132730fcf)

## MODEL COMPARISON
  	
The Adjusted R-squared values in both the initial and reduced models did not change at 0.997 which is extremely high. However, the F-statistic did improve three-fold from 1.388e+05 to 3.547e+05. This shows that there is a much higher significance in the reduced model’s independent variables jointly than with the kitchen sink approach in the initial model (Hayes, A., 2023). 

## RESIDUALS OF THE REDUCED MODEL

![IMG_1612](https://github.com/user-attachments/assets/2f27286e-5658-407c-8b16-cb066dcd1742)

> RSE for Reduced Model:  121.84053033291282


## REGRESSION EQUATION WITH RESULTS OF ANALYSIS

The regression equation in my model is stated below:

> Ŷ = $1,592 + $82.29 (Initial_days) + $226.90 (Comp_risk_numeric) + $515.77 (IA_Emergency) - $14.93 (ReAdmis_Yes) + $110.15 (HighBlood_Yes) + $74.99 (Diabetes_Yes) + $89.99 (Hyperlipidemia_Yes) + $65.58 (Allergic_rhinitis_Yes) + $62.45 (Reflux_esophagitis_Yes) + ε

The coefficients are interpreted as dollar amounts of the given condition. For example, the Initial_days coefficient is 82.29, so that is translated as $82.29 multiplied times the number of days the patient stayed in the hospital. The Comp_risk_numeric coefficient represents the addition of $226.90 multiplied times the patient’s complication risk metric (i.e., 1 – Low, 2 – Medium, 3 – High). Next, was the patient admitted via the Emergency Room (e.g., IA_Emergency)? If so, then the equation adds $515.77. The last six coefficients are all multiplied by 1 if they are present, and are multiplied by 0 if they are not present. 

This reduced model is statistically significant for several reasons. I removed all p-values larger than 0.05 which means that all independent variables are statistically significant. That said, the model performs well given that the Adjusted R-squared value is 0.997. I believe this model is also practically significant for a hospital. This analysis would allow them to perform financial forecasting which would allow hospital leadership to shape the company’s strategic decisions. This analysis could also be used in a marketing strategy to educate patients better on how their overall health is directly correlated to certain high-risk factors. 

There are limitations of this analysis in that by its very nature, multiple linear regression assumes a linear relationship between dependent and independent variables. MLR is also sensitive to outliers in the data, however, I checked each variable for any outliers using boxplots and found there to be only outliers in the Population variable. I treated these outliers, but my final reduced model did not use Population as it was removed during feature selection. I performed backward stepwise elimination to reduce my model. The main limitation to this method is that some variables removed during this process may actually have a causal relationship to the dependent variable, and some variables that were left may have been coincidentally significant, but this method only looks at the p-values to determine significance. 

## RECOMMENDATIONS

I would recommend to the organization that they use the regression equation from my analysis to shape their company’s financial strategies in the future. Using this against their past and present could show trending financial data, and allow them to forecast their financial goals for board members and/or shareholders. 

I would also recommend using this analysis in a marketing program designed to better educate their customers (i.e., patients) on how their overall health is directly correlated to how much their overall bill will be. 

## SUPPORTING DOCUMENTATION

#### SOURCES FOR THIRD-PARTY CODE

Pandas (2023, June 28). Retrieved September 27, 2023, from https://pandas.pydata.org/docs/reference/index.html.

Perktold, J., Seabold, S., & Taylor, J. (2009-2023). Retrieved February 18, 2024, from https://www.statsmodels.org/stable/index.html. 

Waskom, M. (2012-2022). Seaborn Statistical Data Visualization. Retrieved September 27, 2023, from https://seaborn.pydata.org/index.html.

#### SOURCES 

CFA Institute. (2024). Basics of Multiple Regression and Underlying Assumptions. Retrieved January 29, 2024, from https://www.cfainstitute.org/membership/professional-development/refresher-readings/multiple-regression

Massaron, L. & Boschetti, A. (2016). Regression Analysis with Python: Learn the Art of Regression Analysis with Python. Packt Publishing.

Hayes, A. (2023, December 20). Multiple Linear Regression (MLR) Definition, Formula, and Example. Retrieved January 29, 2024, from https://www.investopedia.com/terms/m/mlr.asp 
