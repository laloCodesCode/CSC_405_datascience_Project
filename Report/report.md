---
title: "Data Science Report"
subtitle: "CSC 405-01"
author:
  - Eduardo Herrera-Barraza
  - Kaz Chhan-Kong
  - Lily Nguyen
date: "April 29, 2026"
geometry: margin=1in
papersize: us-letter
fontsize: 12pt
page-numbering: "I"
---

```{=typst}
#set par(leading: 0.65em, spacing: 1.2em, first-line-indent: 0em)
```

```{=typst}
#pagebreak()
```

# Introduction

Fast food consumption has become a defining feature of the typical American diet, particularly among the younger populations. While the general relationship between poor eating habits and adverse health outcomes is widely known, the specific ways in which fast food meal frequency interacts with other lifestyle factors; physical activity, sleep, and BMI, remains worth examining at the individual level.

This report analyzes a dataset of 800 participants containing 11 health and lifestyle variables, including fast food meals per week, BMI, average daily caloric intake, sleep hours, physical activity, and self reported health scores. The goal is to explore whether fast food consumption is a meaningful predictor of overall health or whether health outcomes are better explained by the combination of multiple lifestyle factors.

To answer these questions, we applied data cleaning and explanatory data analysis to understand the structure and distribution of the data, followed by statistical hypothesis testing to evaluate relationships between key variables. The findings aim to provide insight into which factors are most strongly associated with health outcomes in this population.

# Methodology

The dataset used in the analysis contains 800 participant records across 11 health and lifestyle variables, including fast food meal frequency, BMI, average daily caloric intake, physical activity hours, sleep duration, and self reported overall health score. Before any analysis was preformed, the data was examined for quality issues. No missing values or duplicate records were found across any of the 11 columns. Outlier detection was performed on all numeric columns using the interquartile range (IQR), and no statistical outliers were detected. All observed values fell within what is clinically plausible ranges for an adult population, and therefore no records were removed or modified.

Exploratory data analysis was conducted to understand the distribution and relationship within the data, including descriptive statistics for both numeric and categorical variables, group-by aggregations across gender, age group, and digestive issue status, and a correlation matrix across all numeric features. For hypothesis testing, a Pearson correlation test was used to evaluate the linear relationship between fast foods consumption and overall self reported health scores, and an independent samples t-test was conducted to assess whether fast food consumption differed significantly between paraticipants with and without digestive issues. Finally, two predictive models were built and compared; a Decision Tree Regressor and a Random Forest Regressor both trained to predict overall self reported health score from the remaining features, and evaluated using mean squared error (MSE) and $R^2$ score.

# Limitations

There is a major caveat with the manner of how overall health scores were obtained, this score is self reported by the participants. The data is subject to bias, a participant can overstate their health by under reporting their fast food consumption, level of physical activity, and many of the other variables that factor into overall health. Thus, this data is not representative of a broader population since there is no viable way to verify the accuracy of the data and not taking other socioeconomic factors into account.

# Statistical Analysis and Hypothesis Testing

## Pearson Correlation Test

A Pearson Correlation test was performed and modeled as a scatter plot to test the question of _Is there a significant linear relationship between fast food consumption and overall health score?_

_Null Hypothesis ($H_0$) :_ There is NO linear correlation between fast food meals per week and overall health score.

The Peason Correlation test was chosen because both variables are numeric and continuous. Pearson Correlation measures the strength and direction of the linear relationship between the specified variables.

### Results

The results of the Pearson Correlation test came to be a correlation coefficient of 0.0373 and a p-value of 0.2924.

### Analysis

A correlation coefficient of 0.0373 indicates very little to no correlation due to it being near zero. A p-value of 0.2924 is greater than our significance level 0.05, thus we fail to reject the null hypothesis and can conclude that there is NO linear correlation between fast food meals per week and overall health score.

## Correlation Scatter Plot

![Scatter Plot of Fast Food Consumption vs Overall  Health Score](Figures/correlation.png)

### Scatter Plot Interpretation

Based on the scatter plot of Fast Food Consumption vs Overall Health Score, there seems to be no correlation between fast food consumption and overall health score. The scatter plot has no negative or positive direction and the data points are not following a close tight line, indicating of of no correlation between the two variables. The scatter plot shows that for all amounts of fast food eaten, there seeems to be an overall health score across all scores. Based on this scatter plot, it can be stated that fast food consumption has no effect or correlation with overall health score and no linear relationship.

## T test

Fast Food Consumption vs Digestive Issues were then tested and modeled as a violin plot to test the question of _Do people with digestive issues eat more fast food than those without?_

_Null Hypothesis ($H_0$) :_ There is no difference in fast food consumption between individuals with and without digestive issues.

A T test was chosen to see if there is any causation between digestive issues and the amount of fast food meals eaten.

### Results

The results of the T test came to be a t statistic of $t = -1.9239$ and a p-value of $p = 0.0547$.

### Analysis

A t statistic of -1.9239 indicates that group_yes (those with digestive issues) have slightly lower fast food consumption than group_no. A p-value of 0.0547 is greater than our significance level 0.05, thus we fail to reject the null hypothesis and can conclude that there is no difference in fast food consumption between individuals with and without digestive issues. Although the t statistic indicates there is difference in fast food consumption between those with and without digestive issues, the statistical significance comes from the p-value.

## Violin Plot

![Violin Plot of Fast Food Consumption vs Digestive Issues](Figures/violin.png)

### Violin Plot Interpretation

Based on the violin plot of Fast Food Consumption and Digestive Issues, it shows that the overall shapes of both distributions are very similar, indicating that the amount of fast food eaten by those with and without digestive issues are not drastically different. The medians seems to be very close which indicates that both groups tend to eat the same amount of fast food meals. Both groups also have a similar range and spread as well and there is no clear shift or differences in the two groups. From this violin plot, there is no strong evidence that people with digestive issues tend to eat more fast food than those who do not have digestive issues.

# Data Modeling

## Methods

To analyze the relationship between the selected features and the target variable (overall health score), two machine learning models were implemented: a Decision Tree Regressor and a Random Forest Regressor. Key features included lifestyle and demographic factors such as fast food consumption frequency, physical activity level, age, and gender. These variables were selected because they are commonly associated with health outcomes and were available in the dataset after cleaning.

The dataset was first split into training and testing sets using an 80/20 split to ensure that model performance could be evaluated on unseen data. A fixed random seed was applied to ensure reproducibility of results. Prior to modeling, relevant features were selected and cleaned to remove inconsistencies or missing values.

The Decision Tree model works by recursively splitting the dataset into smaller subsets based on feature values, selecting splits that minimize error (measured using mean squared error). However, a single decision tree can be sensitive to noise and may overfit the data.

To address this, a Random Forest model was also implemented. This model builds multiple decision trees using random subsets of the data and features, then averages their predictions. This ensemble approach typically improves generalization and reduces overfitting.

Model performance was evaluated using two metrics:

Mean Squared Error (MSE): Measures the average squared difference between predicted and actual values, the lower the score the better. \
R² Score: Indicates how well the model explains the variance in the target variable. Closer to 1 is better, negative values indicate poor performance.

## Results

The Decision Tree model produced the following results:

- MSE: 8.19
- R²: -0.25

These results indicate that the decision tree performed poorly on the test data. The negative R² score suggests that the model performed worse than simply predicting the mean of the target variable. This is likely due to overfitting, where the model captured noise in the training data but failed to generalize.

The Random Forest model showed improved performance:

- MSE: 6.93
- R²: -0.058

While the random forest reduced the prediction error compared to the decision tree, the R² score is still slightly negative. This indicates that although the ensemble model is more stable and accurate than a single decision tree, it still does not effectively explain the variability in the overall health score.

## Interpretation

Although the Random Forest model improved performance, both models struggled to accurately predict overall health score. This suggests that the selected features such as fast food consumption frequency and physical activity do have some influence, but they are not strong enough on their own to fully explain differences in health outcomes.

The dataset includes factors like sleep, energy level, and physical activity, the models still performed poorly. This suggests that these variables alone are not strong predictors of overall health score, or that other important factors not included in the dataset play a significant role.

# Conclusion

This analysis was conducted to determine whether fast food consumption is meaningful predictor of overall health outcomes. Across all three stages of the analysis the findings consistently pointed to the same conclusion which is the consumption of fast food frequently is not a strong predictor of overall health outcomes.

The Pearson Correlation test yielded no statistically significant relationship between the frequency of fast food consumption and overall health score ($r = 0.0373, p = 0.2924.$). The independent t-test similarly found no significant difference in fast food consumption between those with and without digestive issues ($t = -1.9239, p = 0.0547$). Both predictive models produced negative $R^2$ scores, confirming that the available features were not enough to explain variability in overall health outcomes.

These results suggest that health is multifactorial and cannot be adequately captured by fast food consumption and lifestyle variables alone.
