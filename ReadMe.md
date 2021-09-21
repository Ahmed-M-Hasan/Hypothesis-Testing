# Analyze A/B Test Results
## by Ahmed M. Hassan

## Introduction

This project covers the statistics topics covered in the Udacity Data Analyst Nano-Degree. It covers different topics like probability, hypothesis testing and regression. The project is presented as a jupyter notebook. Through the notebook, the student is asked to answer certain questions that required statistical analysis of provided data.

## Dataset

The data is presented as a CSV file. It contains the data representing an A/B test results to check if a new page design will increase the number of the website visitors who decided to purchase the company products.

## Project Walkthrough

- The project starts with loading the data into `pandas` dataframe for CSV file
- Then, the data is assessed for data quality and tidiness issues. The data is cleaned from the noted issues
- Then, some sample statistics is calculated about the probability of the website visitor purchase a product and the effect of the new design on this probability. These sample satistics can't provide insights about population parameters and statistical inference is required to ensure that the statistics truly represent the actual status of the population and is not caused by chance.
- To perfom a statistical inference a hypothesis testing procedure was followed. The null hypothesis was that the proabability of purchasing a product form the new page design is lower than or equal the old page design. The alternative hypothesis was considering the probability of purchasing products from new page design is higher. 
- The result of this hypothesis testing was that the calculated P-value was 0.9062, the conditional propability of observing the sample statistic or one more extreme in favor of the alternative hypothesis if the null hypothesis is true. Thus, while considering our null hypothesis true, there is a 90.62% to observe the observed difference in the purchasing probability. with type-1 error threshold limited to 5%, we will fail to reject the null hypothesis. This means that the new page purchasing rate for the new page is less than or equal the conversion rate of the old page. The company should not keep the new page as it will be committing type-1 error.
- After that the previous inference was reperformed using logsitic regression. The trained model uses a dummy variable to identify which page the customer landed on, i.e. the old or the new page, to predict if the customer will or will not buy a product. The p-value of that dummy variable showed that this variable is statistically insignificant in predicting if the user will purchase a product or not. This findings supports the result achieved by the hypothesis testing procedure.
- The logisitic regression step was repeated to introduce new dummy variables to represent the customer country. The anaylsis concluded that the country variable is statisitcally insignificant in determining the purchasing probability.

## Conclusions

In this project, the effect of two factors on purchasing probability was investigated. These factors are:
- New web page layout receival
- Country of the user

The `new_page` effect was investigated using z-test of the proportion of conversion between the two groups who receive and didn't receive the new page layout. The test was performed manually and using the built-in function. The results of both confirmed that changing the page doesn't have neither statistical significane nor practical significance on increasing the conversion rate. The null hypothesis stating that the difference in proportions between the two groups is less than of equal zero can't be rejected.<br>

The same conculsion regarding the `new_page` was reached using logistic regression model. The p-value of the predicted coefficient of the dummy variable created to represent receival of the new page indicates that the variable doesn't have statistical significance and there is no effect of receiving the new page on the conversion probability compared with receiving the old page. This experiment was carried out for 21 days and with adequate and nearly equal traffic on both pages layout. All these confirms that the new page layout is not useful and keeping it will be considered type-I error.<br>

The effect of the country and the combined effect of the country with the page layout on the conversion rate was investigated using logistic regression model. The p-values corresponding to the predicted cofficients showed that these variables don't have statistical significance on the conversion rate.

