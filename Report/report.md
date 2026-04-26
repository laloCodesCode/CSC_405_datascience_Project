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

# Graph Interpretations

After the data was cleaned, we visualized it using boxplots to rack if there were any abnormalities or outliers. 

![Boxplot of Data Variables](Images/boxplot1.png)

Based on the boxplot of the data, there are no abnormalities or outliers of any of the variables. 

Fast Food Consumption vs Overall Health Score were then tested and graphed as a scatter plot to see if there was a linear relationship between the two variables. 

![Fast Food Consumption vs Overall Health Score](Images/ffcVsOhs.png)

Based on the scatter plot of Fast Food Consumption vs Overall Health Score, there seems 
to be no correlation between fast food consumption and overall health score. The scatter 
plot has no negative or positive direction and the data points are not following a close 
tight line, indicating of of no correlation between the two variables. The scatter plot shows that for all amounts of fast food eaten, there seeems to be an overall health score across all scores. Based on this scatter plot, it can be stated that fast food consumption has no effect or correlation with overall 
health score and no linear relationship.

Fast Food Consumption vs Digestive Issues were then tested and modeled as a violin plot to see if individuals with digestive issues eat more fast food than those without. 

![Violin Plot of Fast Food Consumption vs Digestive Issues](Images/violin.png)

Based on the violin plot of Fast Food Consumption and Digestive Issues, it shows that the overall shapes of both distributions are very similar, indicating that the amount of fast food eaten by those with and without digestive issues are not drastically different. The medians seems to be very close which indicates that both groups tend to eat the same amount of fast food meals. Both groups also have a similar range and spread as well and there is no clear shift or differences in the two groups. From this violin plot, there is no strong evidence that people with digestive issues tend to eat more fast food than those who do not have digestive issues. 