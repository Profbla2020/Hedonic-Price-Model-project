# Hedonic-Price-Model-project

In the Data Preparation phase for the R Studio analysis, the process started with integrating and 
cleaning the dataset derived from the GIS proximity analysis. This was crucial to ensure the accuracy 
and usability of the data for regression modeling in R. The following steps were undertaken to 

# Prepare the data:
1. Data Loading: The data from the GIS analysis, specifically the proximity metrics of 
micromobility stations to property locations, was imported into R. This was typically done 
using functions like read.csv() for CSV files or read.xlsx() for Excel files, depending on the 
data format provided by the GIS output.

2. Data Inspection and Cleaning: Once loaded, the dataset underwent a thorough inspection to 
identify any inconsistencies, missing values, or outliers that could affect the results of the 
regression analysis. Functions like summary(), str(), and head() were used to get an overview 
of the data structure and to spot any immediate issues.

3. Data Transformation: The dataset required transformations, including the creation of new 
variables that might be more relevant to the analysis, such as calculating the log of property 
prices or categorizing continuous data into meaningful groups. These transformations were 
performed using R’s vectorized operations or the dplyr package for more complex 
manipulations.

4. Handling Missing Data: Missing values were either filled using median or mean imputation 
methods or omitted based on their impact on the dataset's integrity. Decisions on handling 
missing data were guided by the proportion of missing data and its significance to the 
analysis.

5. Data Subsetting: To make the analysis more manageable or focused, the dataset was often 
subsetted based on certain criteria, such as properties within a specific distance range from 
micromobility stations. The subset() function or dplyr filtering methods were instrumental in 
this process.

6. Variable Selection: Based on preliminary analyses and the research objectives, relevant 
variables were selected for inclusion in the regression model. This step was critical to ensure 
that the models were not overfitted and were reflective of the actual dynamics being 
studied.

Each step involved specific R code tailored to the dataset's characteristics and the study's 
requirements, ensuring that the data used in the regression analysis was as accurate and 
representative of the real-world scenarios as possible. This laid the groundwork for the subsequent 
statistical modeling and analysis of how micromobility infrastructure impacts property values in 
London.

# Descriptive Statistics:
1. Summary Statistics : This initial step involves calculating basic summary statistics for key 
variables, such as property prices, distance to micromobility stations, number of bedrooms, 
and property area. These statistics include measures like mean, median, standard deviation, 
and range. This analysis provides an initial understanding of the central tendencies and 
variability within the dataset, which is crucial for setting the stage for more detailed analysis.

2. Visualization of Distributions: To better understand the data distributions, various 
visualizations are utilized, including histograms, boxplots, and density plots. These visual aids 
help in examining the shape, spread, and skewness of the distributions for the main variables. 
They are particularly useful for identifying any potential outliers or anomalies in the data, 
which could impact the validity of subsequent analyses.

3. Quantiles and Percentiles: Quantiles, including quartiles and specific percentiles, are 
calculated to delve deeper into how data points are distributed across the variable range. 
This detailed segmentation helps in understanding the concentration and spread of data 
values, providing insights into the overall distribution characteristics of key variables.

4. Correlation Analysis: Exploring the correlations between variables such as property 
prices and distance to micromobility stations is an essential step. This analysis helps identify 
potential relationships and dependencies between different factors, which could be influential 
in later stages of regression modeling. Understanding these relationships is vital for selecting 
appropriate variables for the regression analysis and for hypothesizing about causal 
relationships.

# Conclusion of Descriptive Statistics:
The descriptive statistics phase is crucial for laying the groundwork for the entire analysis. By 
thoroughly examining the central tendencies, variability, distributions, and relationships within the 
data, this section ensures that the foundation of the dataset is well-understood. This comprehensive 
understanding is essential for guiding the analytical approach in the subsequent modeling phase and 
ensuring that the data's characteristics are well accounted for in the study's broader context. This 
approach not only enriches the analysis but also bolsters the reliability and applicability of the 
findings derived from more complex statistical procedures later in the study.

# Model Building:
In the model-building phase of the analysis, a hedonic pricing model is constructed to understand the 
relationship between property values and their proximity to micromobility infrastructure among 
other features. This method is particularly chosen to decompose the property price into attributes 
that are theoretically priced by the market.

# Selection of Predictors
The selection of predictors for the hedonic pricing model is based on both theoretical frameworks 
and empirical evidence from preliminary analyses (including correlation and descriptive statistics). 
Variables such as distance to nearest micromobility station, number of bedrooms, property area, and 
other relevant factors like age of the property and local amenities are included as predictors. The 
inclusion of these variables is guided by their expected influence on property values and their 
statistical significance in preliminary tests.

# Model Specification
The model is specified using the linear regression function lm() in R, which facilitates the modeling of 
relationships between a dependent variable (property prices) and one or more independent variables 
(predictors). The general form of the hedonic pricing model in this analysis is as follows:
Price = β0 + β1 × Distance to Station + β2 × Bedrooms + β3 × Area + ... + ε
Where:
β0 is the intercept.
β1, β2, β3, ..., are the coefficients for each predictor.
ε is the error term.

Interaction terms may also be included if there is a theoretical justification or if preliminary data 
exploration suggests interactions between variables. For example, an interaction term between 
'distance to station' and 'area' could be included to examine if the effect of proximity to 
micromobility stations on property prices varies by the size of the property.

# Regression Formula
The regression formula is carefully constructed to ensure that all significant predictors are included 
and multicollinearity is minimized. Before finalizing the model, diagnostics are run to check for the 
presence of multicollinearity using variance inflation factor (VIF) scores, and adjustments are made as 
necessary to ensure robust and reliable regression outcomes.

# Building the Model
The actual building of the model involves fitting the specified regression equation to the data using 
the lm() function. The model's output provides coefficients for each variable, which are interpreted 
to understand the impact of each attribute on property prices. This includes examining the signs and 
magnitudes of the coefficients to determine how each characteristic influences the dependent 
variable.

# Model Validation
After the model is built, it undergoes various validation checks including assessing the model fit, 
examining residuals for patterns or anomalies, and conducting tests like the F-test to understand the 
model's explanatory power. These steps are crucial to ensure the model's reliability and to validate 
the assumptions underlying linear regression analysis.

The model-building phase is critical as it translates the conceptual framework and preliminary data 
insights into a quantifiable model that can be empirically tested. This process not only enhances 
understanding of the data but also provides a robust tool for predicting and understanding market 
behaviors in relation to urban micromobility infrastructure and property valuation.

# Model Diagnostics:
Model diagnostics are critical to validate the assumptions underlying the regression model used in 
the analysis. Ensuring that these assumptions hold is key to interpreting the regression results 
confidently. Here are the primary diagnostic tests performed:
1. Linearity
The assumption of linearity implies that there is a linear relationship between the independent 
variables and the dependent variable.To validate this assumption, a plot of observed versus 
predicted values is typically used.
* Plots for Linearity Check: Scatter plots of residuals versus predicted values can be created 
to assess whether the residuals have a non-linear pattern. Ideally, these plots should not 
show any pattern, indicating linearity.
2. Independence
Independence of residuals is crucial for the reliability of the model. Independence implies that the 
residuals are not correlated with each other, an assumption that is particularly important in time 
series or spatial data.

* Durbin-Watson Test: This test checks for autocorrelation in the residuals of a regression 
analysis. A Durbin-Watson statistic near 2.0 suggests no autocorrelation.

3. Homoscedasticity
Homoscedasticity means that the residuals should have constant variance at all levels of an 
independent variable. Heteroscedasticity, where the size of the residuals is related to the size of the 
predictions, can lead to inefficiencies in the regression coefficients.

* Residual vs. Fitted Values Plot: A plot of residuals versus fitted values is used to check for 
homoscedasticity. If the plot shows a funnel shape, it indicates heteroscedasticity, suggesting 
transformations of the dependent variable or the use of robust regression methods might be 
necessary.

4. Normality of Residuals
For many statistical tests to be valid, residuals of the regression should be normally distributed. This 
is crucial for the reliability of the hypothesis tests concerning the regression coefficients.

* Histogram and Q-Q Plots: A histogram of residuals, along with a Quantile-Quantile (Q-Q) 
plot, can be used to assess whether the residuals are normally distributed. The Q-Q plot 
should show that the points fall approximately along a straight line.

5. Multicollinearity
Multicollinearity occurs when two or more predictors in the model are correlated and provide 
redundant information about the response. This can lead to unreliable and unstable estimates of 
regression coefficients.

* Variance Inflation Factor (VIF): Calculating the VIF for each predictor provides a measure of 
the amount of multicollinearity. Typically, a VIF above 5 or 10 indicates a problematic 
amount of collinearity, suggesting that some predictors should be removed or that the 
model should be re-specified.

# Implementing Model Diagnostics in R
In R, these diagnostics can be implemented using various functions and packages. For example, the 
lmtest package can be used for Durbin-Watson tests, and the car package for VIF calculations. Visual 
diagnostics can be facilitated by base R plotting functions or through packages like ggplot2 for 
enhanced visual appeal.
By rigorously performing these diagnostics, you ensure that the model's assumptions are met and 
that the findings are robust and reliable. These checks are not just a good practice but are necessary 
for the model's validation and for the accurate interpretation of its results.

# Model Evaluation:
Evaluating the performance of a regression model is essential to understand how well the model fits 
the data and predicts outcomes. In analysis using R, several statistical metrics are employed to 
assess the model's effectiveness:

1. R-squared (R²)
R-squared is a statistical measure that represents the proportion of the variance in the dependent 
variable that can be explained by the independent variables. It indicates the strength of the 
relationship between your model and the dependent variable, with a higher R-squared value 
suggesting a better fit.

3. Adjusted R-squared
Adjusted R-squared modifies the R-squared to account for the number of predictors in the model. 
This adjustment is crucial when comparing models with different numbers of independent variables, 
as it provides a more accurate measure by incorporating the model's complexity.

5. Root Mean Square Error (RMSE)
RMSE measures the average magnitude of the errors between predicted and observed outcomes, 
providing a sense of how much error the model typically makes in its predictions. Lower values of 
RMSE indicate better predictive accuracy.

# Implementing Model Evaluation in R
The evaluation metrics are typically computed as part of the model output in R:

  * R-squared and Adjusted R-squared are available in the summary output of a regression 
model executed using the lm() function.

  * RMSE is calculated by comparing the model's predicted values to the actual data points. This 
involves extracting predictions from the model and then using them to compute the mean 
squared error, from which the square root is taken to obtain the RMSE.

These metrics together provide a comprehensive evaluation of the model's explanatory power and 
predictive accuracy. They help in assessing how well the model has captured the underlying patterns 
of the data, and whether it generalizes well to new, unseen data. By examining these metrics, you 
can gauge the effectiveness of your model and make informed decisions about potential 
improvements or iterations in your modeling approach. This process ensures that the model not 
only fits the data well but also adheres to the principles of good statistical modeling practice, 
maintaining reliability and accuracy in predictions.

Overall the study effectively combined GIS and R Studio to reveal how micromobility infrastructure 
impacts London's property values. Using GIS for spatial analysis and R for regression modeling, the 
research provided insights into the importance of accessible transportation in urban real estate 
valuation

