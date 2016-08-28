## Categorical Data

### Introduction
  * non-continious
  * can't calculate mean or other similar statistics
  * Mostly dealing with frequencies.

### Contingency table
  A table representing the cross-classification of two or more categorical variables. The levels of each variable are arranged in a grid, and the number of observations falling into each category is noted in the cells of the table.

### Pearson's Chi-squared test ($\chi^2$)
  Does not rely on assumptions such as having continuous normally distributed data (categorical data cannot be normally distributed because they aren’t continuous)

\[
  \chi^2 = \sum\frac{(observed_{ij} - model_{ij})^2}{model_{ij}} \\
  % Expected Frequency \\
  model_{ij} = E_{ij} = \frac{rowTotal_i* colTotal_i}{n}
\]
  $E_{ij}$ is the expected frequency for the cell ${ij}$.

  #### Assumptions of Pearson's Chi-squared test ($\chi^2$)
  * Independence of data
  * Sampling distribution for test statistics has approximate Chi-squared distribution
  * Larger the sample, better the approximation.
  * Small samples, bad approximation causing significance test to be *inaccurate* resulting in **Type 1** error.
  * To use the chi-square test the expected frequencies in each cell must be greater than 5
  * In large samples acceptable to have 20% of frequencies below 5 but none should be below 1.


### Fischer's Exact Test
  * Not much of a test, more a way of calculating exact probability of Chi-squared statistics
  * Normally used with 2 x 2 contigency table with small samples
  * With large table and sample, becomes computationally expensive.

### Likelihood Ratio ($L_{\chi^2}$)
  * Based on maximum-likelihood theory (collect data, create model for which probability of obtaining measured set of data is maximized, & compare model to probability of obtaining those data under null hypothesis).
  * this statistic has a chi-square distribution with the same degrees of freedom
  * For large sample the statistic will be similar to Pearson's but is preferred for small samples

\[
L_{\chi^2} = 2(\sum{Observed_{ij}ln(\frac{observed_{ij}}{model_{ij}}}))
\]

### Yate's (Continuity) Correction
  Subtracts 0.5 from the deviance calculation
  \[
  \chi^2 = \sum\frac{(|observed_{ij} - model_{ij}| - 0.5)^2}{model_{ij}} \\
  \]


### Calculating in R
  Function: CrossTable
  Package: gmodels
  Output cell contents:
  * Count
  * Expected value
  * Chi-squared contribution
  * Row Percent
  * Col Percent
  * Total Percent
  * Std Residual

### Standardized Residual
  Chi-squared statistics is sum of all Standardized residuals.
  Standardized Residual behaves like **z-scores**

  \[
  Residual = observed_{ij} - model_{ij} \\
  Standardized Residual = \frac{observed_{ij} - model_{ij}}{\sqrt{model_{ij}}}
  \]

### Odds Ratio (Effect Size)
  Effect size for *Categorical Variables* are measured as **Odds Ratio**
  Effect sizes are only ever useful when they summarize a focused comparison.
  \[
  Odds Ratio = \frac{Odds_{variableA}}{Odds_{variableB}}
  \]

### Reporting results of Chi-squared
  Example:
  > There was a significant association between the type of training and whether or not cats would dance χ2(DF) = Chi-squared, p < 0.001 (χ2(1) = 25.36, p < .001). This seems to represent the fact that, based on the odds ratio, the odds of cats dancing were Odds_Ration (Confidence Interval) (6.58 (2.84, 16.43)) times higher if they were trained with food than if trained with affection.
