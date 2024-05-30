#EXPLORATORY DATA ANALYSIS AND REGRESSION MODELING OF HOUSING PRICES IN STATA

Given,
price = β0 + β1lotsize + β2sqrft + β3bdrms + β4colonial + e
Where,
price= house price, $1000s
bdrms= number of bedrooms
lotsize=size of lot in square feet
sqrft = size of house in square feet
colonial=1 if home is colonial style 
Task 1: Describe variables

Code: 
describe price bdrms lotsize sqrft colonial
![image](https://github.com/EDGEofMRI/EXPLORATORY-DATA-ANALYSIS-AND-REGRESSION-MODELING-STATA/assets/18722680/d73521b3-7ab0-44da-9c5a-c76de4032448)

 
	price: This is a float type variable that represents the house price in thousands of dollars.
	bdrms: A byte type variable indicating the number of bedrooms in a house.
	lotsize: Another float type variable, denoting the size of the lot in square feet.
	sqrft: An integer type variable that signifies the size of the house in square feet.
	colonial: A byte type variable where a value of 1 indicates the home is colonial style.

Task 2: Descriptive statistics

Code: 
summarize

![image](https://github.com/EDGEofMRI/EXPLORATORY-DATA-ANALYSIS-AND-REGRESSION-MODELING-STATA/assets/18722680/b4c54ff0-7efc-4acc-a0b4-f9126a08f758)

	Variable: This column lists the names of the variables included in the dataset, such as price, assess, bdms, lotsize, and sqft.
	Obs (Observations): Indicates the number of observations or entries for each variable. In this case, each variable has 88 observations.
	Mean: The average value for each variable. For example, the mean number of bedrooms (bdrms) is approximately 3.57.
	Std. dev. (Standard Deviation): Measures the amount of variation or dispersion from the mean. A higher standard deviation indicates more spread-out values.
	Min (Minimum): The smallest value observed for each variable.
	Max (Maximum): The largest value observed for each variable.

Task 3: Descriptive statistics for colonial and non-colonial style separately

Code: 
summarize lotsize sqrft bdrms if colonial == 1
summarize lotsize sqrft bdrms if colonial == 0

![image](https://github.com/EDGEofMRI/EXPLORATORY-DATA-ANALYSIS-AND-REGRESSION-MODELING-STATA/assets/18722680/de6f105a-0471-4d47-9d7c-91025e16312d)


	Variable: This column lists the names of the variables included in the dataset, such as lotsize, sqft (square feet), and bdrms (bedrooms).
	Obs (Observations): Indicates the number of observations or entries for each variable. In this case, there are two sets of observations, one for when “colonial” equals 1 and another for when “colonial” equals 0.
	Mean: The average value for each variable. For example, the mean lot size when “colonial” equals 1 is approximately 9,114 square feet.
	Std. dev. (Standard Deviation): Measures the amount of variation or dispersion from the mean. A higher standard deviation indicates more spread-out values.
	Min (Minimum): The smallest value observed for each variable.
	Max (Maximum): The largest value observed for each variable.


Task 4: Boxplot of price and five-summary measures

Code:
graph box price
summarize price, detail
 
![image](https://github.com/EDGEofMRI/EXPLORATORY-DATA-ANALYSIS-AND-REGRESSION-MODELING-STATA/assets/18722680/84f22818-f51c-4538-bf67-e8b2356450be)

	Median House Price: The line inside the blue box represents the median house price, which is around \$350,000.
	Quartiles: The edges of the box indicate the lower and upper quartiles of the house prices.
	Outliers: The individual points above \$600,000 are outliers, indicating houses that are priced significantly higher than most others in the dataset.
 
Box plots are great for visualizing the spread and skewness of data, as well as identifying outliers. They provide a clear summary of the central tendency and variability of the data.
![image](https://github.com/EDGEofMRI/EXPLORATORY-DATA-ANALYSIS-AND-REGRESSION-MODELING-STATA/assets/18722680/585cb779-1a5a-48f9-9bfb-a8e7ba9cbd8e)

	Percentiles: These values give you a sense of the distribution of house prices. For example, the 50th percentile (median) is $265.5k, meaning that half of the houses are priced below this value.
	Smallest and Largest Prices: The smallest recorded price is $111k, and the largest is $725k.
	Mean: The average house price is approximately $293.546k.
	Standard Deviation: This is about $102.7134k, indicating the average amount by which house prices deviate from the mean.
	Variance: At 10550.05, it measures the spread of house prices.
	Skewness: A value of 1.998857 suggests that the distribution of house prices is right-skewed, meaning there are a few houses with prices much higher than the rest.
	Kurtosis: A value of 8.393914 indicates a “leptokurtic” distribution, meaning the distribution has heavier tails and a sharper peak than the normal distribution.

Task 5: Graph of mean price by number of bedrooms

Code:
graph bar (mean) price, over(bdrms) title(Mean Price by Number of Bedrooms) ytitle(Price)
 
![image](https://github.com/EDGEofMRI/EXPLORATORY-DATA-ANALYSIS-AND-REGRESSION-MODELING-STATA/assets/18722680/7d7e0cb2-7ffb-428a-8ca2-c29a5727bd00)

It illustrates how the mean price of properties changes with the number of bedrooms. Here's a summary of the information presented:
	2 and 3 Bedrooms: Properties with 2 and 3 bedrooms have similar mean prices, around \$200,000.
	5 Bedrooms: There's a significant increase in mean price for properties with 5 bedrooms, reaching close to \$500,000.
	4 and 6 Bedrooms: The mean prices for properties with 4 and 6 bedrooms are lower than those with 5 bedrooms, ranging approximately between \$300,000 and \$400,000.
	7 Bedrooms: Properties with seven bedrooms show an increase in mean price again but do not reach as high as those with five bedrooms.

Task 6:
Plot the dependent variable against each independent variable

Code:
twoway (scatter price lotsize) (lfit price lotsize), title("Price vs Lot Size")
twoway (scatter price sqrft) (lfit price sqrft), title("Price vs Square Feet")
twoway (scatter price bdrms) (lfit price bdrms), title("Price vs Bedrooms")
twoway (scatter price colonial), title("Price vs Colonial Style")

 ![image](https://github.com/EDGEofMRI/EXPLORATORY-DATA-ANALYSIS-AND-REGRESSION-MODELING-STATA/assets/18722680/781adbec-cf5b-428a-8d85-0283f5918490)

Illustrates the relationship between the size of a lot and the corresponding house price. Here's a summary of its key points:
	X-Axis (Lot Size): Ranges from 0 to 100,000 square feet.
	Y-Axis (House Price): Ranges from \$0 to \$800,000.
	Data Points: Represent individual house prices at various lot sizes, with most clustered around lower prices and smaller lot sizes.
	Trend Line (Fitted Values): Indicates an upward trend, showing that as the lot size increases, the house price tends to increase as well.

![image](https://github.com/EDGEofMRI/EXPLORATORY-DATA-ANALYSIS-AND-REGRESSION-MODELING-STATA/assets/18722680/99a9438e-bcea-4984-ab9d-9f752ada16d4)

Illustrates the relationship between the size of a house (in square feet) and its price (in $1000s). Here's a summary of its key points:
	X-Axis (Size of House): Ranges from 1,000 to 4,000 square feet.
	Y-Axis (House Price): Ranges from \$0 to \$800,000.
	Data Points: Blue dots represent individual houses, showing the combination of house sizes and prices.
	Trend Line (Fitted Values): The red line indicates an upward trend, suggesting that as the square footage of a house increases, the price tends to increase as well.

 ![image](https://github.com/EDGEofMRI/EXPLORATORY-DATA-ANALYSIS-AND-REGRESSION-MODELING-STATA/assets/18722680/4fb67f88-f909-47fd-b214-81a46151ee53)

The graph shows the relationship between house prices and the number of bedrooms. Here's a quick interpretation:
	X-Axis (Number of Bedrooms): Ranges from 2 to 7 bedrooms.
	Y-Axis (House Price): Ranges from \$0 to \$800,000, with prices indicated in thousands of dollars.
	Data Points: Blue dots represent individual houses, showing the price for the corresponding number of bedrooms.
	Trend Line (Fitted Values): The red line indicates an overall increasing trend, suggesting that generally, as the number of bedrooms increases, the house price tends to increase as well.

![image](https://github.com/EDGEofMRI/EXPLORATORY-DATA-ANALYSIS-AND-REGRESSION-MODELING-STATA/assets/18722680/d7ed9511-fd81-4103-baa7-7a2e31d41360)
 
The scatter plot shows the relationship between house prices and whether the home is built in a colonial style. Here's a breakdown of its key features:
	X-Axis: Indicates whether a home is colonial style, with values 0 for non-colonial and 1 for colonial.
	Y-Axis: Represents the house price in thousands of dollars, ranging from \$0 to \$800,000.
	Data Points: There are two clusters of data points. One cluster for non-colonial style homes is towards the lower end of the price range, while the cluster for colonial style homes is towards the higher end.
This graph suggests that colonial-style homes are generally priced higher than non-colonial ones. It's a clear visual representation of how a specific style of home can influence its market price.

Task 7: Linear regression of the specified model

Code:
reg price lotsize sqrft bdrms colonial

![image](https://github.com/EDGEofMRI/EXPLORATORY-DATA-ANALYSIS-AND-REGRESSION-MODELING-STATA/assets/18722680/d927993f-9479-4cf1-881c-0b681ec420aa)
 
The relationship between the price of houses and various factors such as lot size, square footage, bedrooms, and whether the house is colonial style. Here’s a brief explanation of the key elements:
	Model Summary: This section provides an overview of the regression model’s performance, including the number of observations (88), the F-statistic, the p-value associated with the F-statistic (Prob > F), and measures of model fit like R-squared and Adjusted R-squared. The Root Mean Squared Error (Root MSE) is also provided.
	Coefficients: This part of the output shows the estimated effect of each variable on the price. For instance, the coefficient for lot size suggests that for each additional square foot of lot size, the price increases by approximately 0.0021 thousand dollars (or $2.10).
	Statistical Significance: The p-values (P>|t|) indicate whether the coefficients are statistically significant. For example, the p-value for square footage (sqft) is 0.000, which is typically considered statistically significant, suggesting that square footage is a strong predictor of house price.
	Confidence Intervals: These provide a range within which the true coefficient value is likely to fall with a certain level of confidence (usually 95%).

Task 8: Interpretation of the coefficient of sqrft and bdrms
	sqrft: The coefficient of sqrft is 0.1242. This means that for every one unit increase in square footage, the price of the house is expected to increase by approximately $124.24 (in $1000s), holding all other variables constant. 
	bdrms: The coefficient of bdrms is 11.0043. This suggests that for every additional bedroom, the price of the house is expected to increase by $11,004.30 (in $1000s), holding all other variables constant.

Task 9: Interpretation of the y-intercept
The y-intercept (-24.12653) represents the estimated price of a house with zero square footage, zero lot size, zero bedrooms, and non-colonial style. However, this interpretation may not be practically meaningful as such a scenario is not realistic.

Task 10: Test individually at 1% level of significance whether each independent variable has a statistically significant relation with the price.

Code:
Test for significance of lotsize coefficient
test lotsize
Test for significance of sqrft coefficient
test sqrft
Test for significance of bdrms coefficient
test bdrms
Test for significance of colonial coefficient
test colonial
To test individually whether each independent variable has a statistically significant relationship with the price at the 1% level of significance, we perform hypothesis tests for each coefficient. Here are the null and alternative hypotheses for each independent variable:
	Null Hypothesis (H_0): The coefficient of the independent variable is equal to zero.
	Alternative Hypothesis (H_1): The coefficient of the independent variable is not equal to zero.
Let's perform the tests:
	For lotsize, the null hypothesis is H_0: β_lotsize=0 and the alternative hypothesis is H_1: β_lotsize≠ 0.
	For sqrft, the null hypothesis is H_0: β_sqrft=0and the alternative hypothesis is H_1: β_sqrft≠ 0
	For bdrms, the null hypothesis is H_0: β_bdrms=0and the alternative hypothesis is H_1: β_bdrms≠ 0.
	For colonial, the null hypothesis is H_0: β_colonial=0 and the alternative hypothesis is H_1: β_colonial≠ 0.
If the p-value is less than 0.01, we reject the null hypothesis and conclude that the independent variable has a statistically significant relationship with the price at the 1% level of significance.

![image](https://github.com/EDGEofMRI/EXPLORATORY-DATA-ANALYSIS-AND-REGRESSION-MODELING-STATA/assets/18722680/ce79350a-bfb0-4495-b831-c1caea1dd26d)
 
	lotsize: Tested to see if it significantly predicts the dependent variable. With an F-statistic of 10.43 and a p-value of 0.0018, it is statistically significant, suggesting lot size is a meaningful predictor in the model.
	sqrtf (square footage): Also significant with an F-statistic of 86.76 and a p-value of 0.0000, indicating square footage is a strong predictor of the dependent variable.
	bdrms (bedrooms): Not statistically significant with an F-statistic of 1.34 and a p-value of 0.2508, implying the number of bedrooms is not a significant predictor in this model.
	colonial: The colonial variable is not significant either, with an F-statistic of 0.88 and a p-value of 0.3515, indicating that whether a house is colonial style or not does not significantly predict the dependent variable.

Task 11: Test at 1% level of significance whether all the independent variables together have any statistically significant relation with the price.

Code:
Test for overall significance of the regression model
testparm lotsize sqrft bdrms colonial

To test whether all the independent variables together have any statistically significant relation with the price at the 1% level of significance, we can perform an overall F-test for the regression model.
Here are the null and alternative hypotheses:
	Null Hypothesis (H_0): All coefficients of the independent variables are equal to zero simultaneously.
	Alternative Hypothesis (H_1):  At least one of the coefficients of the independent variables is not equal to zero.
We'll use the overall F-test associated with the regression model to test these hypotheses.
If the p-value is less than 0.01, we reject the null hypothesis and conclude that at least one independent variable has a statistically significant relationship with the price at the 1% level of significance.

![image](https://github.com/EDGEofMRI/EXPLORATORY-DATA-ANALYSIS-AND-REGRESSION-MODELING-STATA/assets/18722680/da6413fa-e232-4d8a-a7b2-3b05b30af1c4)

The results of a hypothesis test for a regression model. The test is examining whether the coefficients for the variables lotsize, sqft (square footage), bdrms (bedrooms), and colonial are significantly different from zero.
Here’s a breakdown of the output:
	Variables Tested: lotsize, sqrft, bdrms, colonial.
	Hypothesis: The null hypothesis being tested is that each of these coefficients is equal to zero, which would imply they have no effect.
	F-Statistic: The F-statistic is 43.25, which is used to determine the test’s p-value.
	Degrees of Freedom: The degrees of freedom for this test are (4, 83), indicating that there are four parameters being tested and 83 observations.
Prob > F: The probability of observing a value of the F-statistic as extreme as 43.25 under the null hypothesis is less than 0.0001.
Interpretation: Since the p-value is less than 0.0001, we reject the null hypothesis that all of the coefficients are equal to zero. This suggests that at least one of the variables has a significant relationship with the dependent variable in the model.

Task 12: The value of the Adjusted R-square and Interpretation of the value of Adjusted R-square.
The value of the adjusted R-square is provided in the regression output. It is a measure of the proportion of variance in the dependent variable that is explained by the independent variables, adjusted for the number of predictors in the model.
In the regression output, the adjusted R-square value is 0.6602.
Interpreting the adjusted R-square value:
Adjusted R-square is a modified version of R-square that adjusts for the number of predictors in the model. It penalizes the addition of unnecessary predictors that do not significantly improve the model's explanatory power. The adjusted R-square typically increases when a new predictor improves the model's fit and decreases when adding a new predictor doesn't improve the fit.
In this context, an adjusted R-square value of 0.6602 indicates that approximately 66.02% of the variability in house prices is explained by the independent variables (lotsize, sqrft, bdrms, and colonial) included in the model, adjusted for the number of predictors. This means that the model, as it stands, explains about 66.02% of the variability in house prices, which is a moderately high level of explanatory power.

Task 13: Additional
Plot residuals versus fitted values
 
Code:
rvfplot

![image](https://github.com/EDGEofMRI/EXPLORATORY-DATA-ANALYSIS-AND-REGRESSION-MODELING-STATA/assets/18722680/fad30a0e-5b53-4a98-98d5-b1af32c85418)

The graph is a residual plot, which is used in regression analysis to visualize the errors between observed and predicted values. Here's what the graph indicates:
	X-Axis (Fitted Values): Represents the predicted values from the regression model, ranging from 200 to 600.
	Y-Axis (Residuals): Represents the differences between the observed values and the fitted values, ranging from -100 to 200.
	Data Points: The blue dots scattered across the graph show the residuals for different fitted values.
Residual plots are important for diagnosing regression models. They help to check whether the errors are randomly distributed, which is an assumption of linear regression. If the residuals display a pattern (like a curve or clustering), it suggests that the model may not be appropriate for the data.

Test for multicollinearity using VIF

Code:
vif

![image](https://github.com/EDGEofMRI/EXPLORATORY-DATA-ANALYSIS-AND-REGRESSION-MODELING-STATA/assets/18722680/800307b5-c006-43f5-b6a0-59a36d4c7f23)

The table shows the Variance Inflation Factor (VIF) for four variables: bedrooms (bdrms), square footage (sqrft), colonial style (colonial), and lot size (lotsize). Here’s what the VIF values indicate:
	VIF: It measures how much the variance of an estimated regression coefficient increases due to multicollinearity. A VIF value greater than 10 is often considered indicative of high multicollinearity.
	1/VIF: This is the reciprocal of the VIF and is used to assess the severity of multicollinearity. Higher values (closer to 1) are better.
Here are the VIF details from table:
	bdrms: VIF = 1.56, which suggests a moderate amount of multicollinearity.
	sqrft: VIF = 1.44, also indicating a moderate amount of multicollinearity.
	colonial: VIF = 1.12, suggesting low multicollinearity.
	lotsize: VIF = 1.04, suggesting very low multicollinearity.
The mean VIF of 1.29 for all variables indicates that multicollinearity is not a major concern for your model. Generally, if the mean VIF is well below 5, the regression coefficients are considered to be well-estimated despite the presence of multicollinearity.

Test for normality of residuals using Q-Q Plot

Code:
predict resid, residual
qnorm resid

![image](https://github.com/EDGEofMRI/EXPLORATORY-DATA-ANALYSIS-AND-REGRESSION-MODELING-STATA/assets/18722680/f1c4b63c-b002-47c5-b63a-194e51a9dad9)

 
The graph is a quantile-quantile (Q-Q) plot, which is used to assess whether the residuals from a statistical model are normally distributed. Here's what the graph indicates:
	X-Axis (Inverse Normal): Represents the theoretical quantiles from a normal distribution, ranging from -200 to 200.
	Y-Axis (Residuals): Represents the residuals from your model, ranging from -100 to 200.
	Data Points: The blue dots are the actual residuals plotted against the expected normal distribution values.
	Trend Line: The green line represents the expected line if the residuals were perfectly normally distributed.
In a Q-Q plot, if the data points closely follow the trend line, it suggests that the residuals are approximately normally distributed. This is important because many statistical tests assume normality of residuals. Deviations from the line, especially at the ends, could indicate skewness or outliers in the data.

Task 14: Perform regression with logarithmic transformations

Code:
reg lprice llotsize lsqrft bdrms colonial

Generate fitted values and residuals for the new regression model

Code:
predict resid, residuals
predict fitted, xb
Plot residuals versus fitted values
Code:
scatter resid fitted, title("Residuals vs Fitted Values") xtitle("Fitted Values") ytitle("Residuals")

![image](https://github.com/EDGEofMRI/EXPLORATORY-DATA-ANALYSIS-AND-REGRESSION-MODELING-STATA/assets/18722680/392c0cf1-d77c-49f8-bc63-44ae957074db)
 
The results of a hypothesis test for a regression model. The test is examining whether the coefficients for the variables lotsize, sqft (square footage), bdrms (bedrooms), and colonial are significantly different from zero.
	Variables Tested: lotsize, sqrft, bdrms, colonial.
	Hypothesis: The null hypothesis being tested is that each of these coefficients is equal to zero, which would imply they have no effect.
	F-Statistic: The F-statistic is 43.25, which is used to determine the test’s p-value.
	Degrees of Freedom: The degrees of freedom for this test are (4, 83), indicating that there are four parameters being tested and 83 observations.
	Prob > F: The probability of observing a value of the F-statistic as extreme as 43.25 under the null hypothesis is less than 0.0001.
Interpretation: Since the p-value is less than 0.0001, we reject the null hypothesis that all of the coefficients are equal to zero. This suggests that at least one of the variables has a significant relationship with the dependent variable in the model.

 ![image](https://github.com/EDGEofMRI/EXPLORATORY-DATA-ANALYSIS-AND-REGRESSION-MODELING-STATA/assets/18722680/3df26bd2-cb4c-474f-8259-9a375b0c0bb4)

The graph is used in regression analysis to assess the goodness-of-fit of a model. Here's a brief explanation of its components:
	X-Axis (Fitted Values): Represents the predicted values from the regression model, typically ranging from the minimum to the maximum predicted values.
	Y-Axis (Residuals): Represents the differences between the observed values and the fitted values, which are the residuals.
	Data Points: The blue dots scattered across the plot show the residuals for different fitted values.
In a well-fitting model, we expect the residuals to be randomly scattered around the horizontal axis (zero line), with no clear pattern. This would indicate that the model's predictions are accurate on average. However, if there's a clear pattern or systematic structure to the residuals, this suggests that the model may not be capturing some aspect of the data's structure, and a different model might be needed.
Result: As the blue dots scattered across the plot with no clear pattern, this indicates the model’s predictions are accurate on average.




Thank You
