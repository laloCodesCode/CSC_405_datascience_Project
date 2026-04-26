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

# Data Modeling

#### Methods

To analyze the relationship between the selected features and the target variable (overall health score), two machine learning models were implemented: a Decision Tree Regressor and a Random Forest Regressor. Key features included lifestyle and demographic factors such as fast food consumption frequency, physical activity level, age, and gender. These variables were selected because they are commonly associated with health outcomes and were available in the dataset after cleaning.

The dataset was first split into training and testing sets using an 80/20 split to ensure that model performance could be evaluated on unseen data. A fixed random seed was applied to ensure reproducibility of results. Prior to modeling, relevant features were selected and cleaned to remove inconsistencies or missing values.

The Decision Tree model works by recursively splitting the dataset into smaller subsets based on feature values, selecting splits that minimize error (measured using mean squared error). However, a single decision tree can be sensitive to noise and may overfit the data.

To address this, a Random Forest model was also implemented. This model builds multiple decision trees using random subsets of the data and features, then averages their predictions. This ensemble approach typically improves generalization and reduces overfitting.

Model performance was evaluated using two metrics:

Mean Squared Error (MSE): Measures the average squared difference between predicted and actual values, the lower the score the better. \
R² Score: Indicates how well the model explains the variance in the target variable. Closer to 1 is better, negative values indicate poor performance.

#### Results

The Decision Tree model produced the following results:

- MSE: 8.19
- R²: -0.25

These results indicate that the decision tree performed poorly on the test data. The negative R² score suggests that the model performed worse than simply predicting the mean of the target variable. This is likely due to overfitting, where the model captured noise in the training data but failed to generalize.

The Random Forest model showed improved performance:

- MSE: 6.93
- R²: -0.058

While the random forest reduced the prediction error compared to the decision tree, the R² score is still slightly negative. This indicates that although the ensemble model is more stable and accurate than a single decision tree, it still does not effectively explain the variability in the overall health score.

#### Interpretation

Although the Random Forest model improved performance, both models struggled to accurately predict overall health score. This suggests that the selected features such as fast food consumption frequency and physical activity do have some influence, but they are not strong enough on their own to fully explain differences in health outcomes.

The dataset includes factors like sleep, energy level, and physical activity, the models still performed poorly. This suggests that these variables alone are not strong predictors of overall health score, or that other important factors not included in the dataset play a significant role.

# Conclusion
