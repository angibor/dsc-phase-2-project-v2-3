# Phase 2 Project Submission

Students names: Angella Bor | Jackline Njuguna | Vitelis Siocha | Mwenda Mugambi
Student pace: Part time

## Project Overview

We conducted a comprehensive analysis of house sales data in a northwestern county using multiple linear regression modeling. Our goal was to gain insights into the factors that affect house prices and develop a predictive model that can estimate the value of homes based on various features.

## Deliverables

There are three deliverables in this project:

* A **non-technical presentation**
* A **Jupyter Notebook**
* A **GitHub repository**

### Business Problem

. Weichert Realtors needs to provide valuable advice to homeowners regarding how home renovations may impact the estimated value of their homes and by what amount.
. By addressing this problem, Weichert Realtors can offer valuable guidance to homeowners, strengthen their relationships with clients, and potentially increase their     
business.

Questions to answer:

1. What influence does the qualitative aspects of a house have on its sale price?
2. Is there a correlation between quantitative features and the selling price of a house?
3. What suggestions can be made to property investors seeking to optimize their returns from commercial real estate investments?

### Data Exploration

 . In this section we went through the data sets we have to understand the structure and determine the ones we'll be using for this project.
 1. We started by importing the libraries and the datasets that will be necessary for the process.
 2. We imported the data set "data/kc_house_data.csv"
 3. Checked the shape of our data using data.shape
 4. Getting a quick overview of our data data.info()

. From the output, we can see that several columns have missing values, such as 'waterfront', 'view' and 'yr_renovated'. We also noticed 'sqft_basement' datatype is not an object as expected.

## Data Processing
1. We addressed Dtypes issue in "sqft_basement" by replacing the "?" with the mode using the .replace function.
2. We also filled the missing values

. The next step was getting a quick overview of the distribution and central tendency of the data to get more nsights into the dataset's characteristics and came up with the following findings;-
i. Home prices range from 78,000 - 7,700,000
ii. The mean house price in the dataset is approximately $540,296.
iii. Most houses have between 3 and 4 bedrooms on average (mean of approximately 3.37)
iv. There is also a maximum of 33 bedrooms-(This could be an outlier or a data entry error.)
v. The average number of bathrooms is approximately 2.12, with a range from 0.5 to 8 bathrooms per house.
vi. The houses in the dataset were built over a wide time span, with a mean construction year of around 1971, suggesting both older and newer properties.
vii. Most houses have 1.494 floors on average, with a minimum of 1 floor and a maximum of 3.5 floors.

NB: We confirmed that the 33 bedrooms is an outlier, using a boxplot.

* Overview
* Business and Data Understanding
  * Explain your stakeholder audience here
* **Modeling**
* **Regression Results**
## EXPLORATORY DATA ANALYSIS
1. We checked how the house price relate with continuous features by checking the following relationships.
   
a. Relationship Between Price and Number of Bathrooms
b. Relationship Between Price and Square footage of living space in the home
c. Relationship Between Price and Square footage of house apart from basement
d. Relationship Between Price vs Square footage of the basement
e. Relationship Between Price vs Number of floors (levels) in house
f. Relationship Between Price vs Square footage of the lot

2. We also checked how the house price relate with qualitative features.

a. Relationship house views condition and price
b. Relationship Between House condition and price
c. Relationship Between house with waterfronts and price

## MODELING
1. Correlation of other features/variables with House Price
a. We calculated the correlation matrix
b. We got the correlation of 'price' with all other columns

2. We checked the most correlated column feature with price?

3. We also checked What is the most correlated feature with other features excluding price.

## Findings 
The most collerated feature with other features excluding price is 'sqft_living'. Since 'sqft_living' has two most auto-correlation with other features after price, we will drop it to avoid multicollinearity issues when modelling.

## 1. Base Model
## 1. Baseline Model
We have found our most correlated column with price is 'grade', therefore we built our Baseline model with this column. Our baseline model is a simple linear regression that take the equation;
Y= aX+b

In this equation:
Y is the dependent variable ('price').

X is the independent variable ('grade').

a is the slope of the regression line, representing the change in Y for a one-unit change in X. It is also known as the regression coefficient or the coefficient of the independent variable.

b is the y-intercept, representing the value of Y when X is zero.

## We set up variable, fitting linear regression model and viewing the model results by;-
a. Declaring Variables
b. Fitting model

## Summary findings and interpretation
The linear regression model fitted above uses the 'grade' as the independent variable to predict the 'price' of houses. The R-squared value of 0.446 indicates that approximately 44.6% of the variance in house prices can be explained by the 'grade.' The coefficient for 'grade' is 209,200, suggesting that, on average, a one-unit increase in the 'grade' results in an increase of $209,200 in the house price. The constant term of -1,062,000 represents the estimated price when 'grade' is zero. The p-values are close to zero, indicating that the 'grade' is statistically significant in predicting house prices. The model fits the data well, although there might be some multicollinearity concerns, given the high coefficient value for 'grade.'

## 2. Multiple Linear Regression Model
The four assumptions kept for multiple Linear Regression Models below include:

i. No multicollinearity
ii. Linear relationship between explanatory and response variables
iii. Homoscedasticity of error terms
iv. Normal distribution of model residuals

## a. Using Continuous data and Categorical features to build multiple regression models we did the following;-
i. Model Continuous features and grade column
ii. Model Continuous features and house condition feature
This second model, which includes the categorical variable condition along with continuous variables, shows an R-squared of 0.511, indicating 51.1% of price variance explained. All predictors are statistically significant. This model performs similarly to the previous one, suggesting condition may be a valuable predictor alongside the other features. THis model performs better than the baseline model.

## b. Model using only categorical features
The third model, using only categorical features (condition, waterfront, grade, view), has an R-squared of 0.525, explaining 52.5% of price variance. All categorical predictors are statistically significant below the chosen p_value of 0.05. This model simplifies the model significantly and performs competitively, suggesting that categorical features alone can provide valuable predictive power.

## c. Model using only continuous variables
The fourth model, utilizing only continuous variables, demonstrates an R-squared value of 0.584, indicating that 58.4% of the variance in price is explained. All continuous variables are statistically significant predictors of price. This model outperforms the previous models, suggesting that using only continuous features provides a strong predictive power for price. However, multicollinearity is a potential issue.

## d. Model using specific continuous variables
The fifth model, using specific continuous variables (bedrooms, bathrooms, sqft_lot, sqft_basement, sqft_above, floors), exhibits an R-squared value of 0.843, indicating a high explanatory power of 84.3%. All selected continuous variables are statistically significant. The model performs exceptionally well, but the absence of a constant term may affect its generalizability. Thus, we consider evaluating its performance on a validation dataset to ensure its validity given that this is the only model that has strongly fitted the data with high explanatory power of more than eighty percent. However.

## We now checked the Performance of the fifth model.
We first split the data into training and validation sets using train_test_split. Then, we train the model using the training data. Finally, we make predictions on the validation set and evaluate the model's performance.

The fifth model, using specific continuous variables, achieves an impressive R-squared value of 0.844 on the validation set. This indicates that approximately 84.4% of the variance in housing prices is explained by the model. The chosen features (bedrooms, bathrooms, sqft_lot, sqft_basement, sqft_above, floors) are highly influential in predicting prices.

## Conclusion
Significant Predictors: The regression models revealed that certain features strongly influence house prices. These include the number of bedrooms, bathrooms, square footage, condition, grade, and view. However, number of bedrooms, bathrooms, Square footage of the lot, Square footage of the basement, Square footage of house apart from basement and Number of floors (levels) in house seemed to be the best in explaining the house prices.

High Predictive Power: The best-performing model, using specific continuous variables mentioned above, achieved an R-squared value of 0.844, indicating that approximately 84.4% of the variance in housing prices can be explained by the model.

## Recommendations:
Based on the analysis, several recommendations can be made to assist homeowners and Weichert Realtors:

a. Renovations Impact on Price: Emphasize the importance of specific renovations, such as increasing number of bedrooms, bathrooms, Square footage of the lot, Square footage of the basement, Square footage of house apart from basement and Number of floors (levels) in house

b. Maximizing ROI: Advise homeowners on renovations that are likely to yield the highest return on investment.

c. Consider Square Footage: Highlight the significance of square footage in determining the value of a property.
