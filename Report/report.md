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

# Conclusion
