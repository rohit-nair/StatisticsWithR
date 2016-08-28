# Test of association

## Covariance
  Covariance of two variables can be tested in the same fashion as we calculate variance namely:
  \[
    cov(x,y) = \frac{\sum(X - \bar{X})(Y - \bar{Y})}{(N-1)}
  \]
  Problem with covariance is that it's dependent on scale of measure. If the units change then the value for *cov* changes.

## Standardization and Pearson's Correlation Coefficient
  * Due to dependence of covariance on unit, a standardized measure is required.
  * The unit of measure used is *Standard Deviation*
  * So covariance is divided by SD to get deviation from mean.
  \[
    r = \frac{cov(x,y)}{s_{x}s_{y}} = \frac{\sum(X - \bar{X})(Y - \bar{Y})}{(N-1)s_{x}s_{y}}
  \]

  * Pearson's Correlation Coefficient (*r*) lies between -1 & 1
  * *r* is also used to measure *Effect Size* as it's standardized measure of effect.
  -0.1 < r < 0.1 = **Small Effect**
  -0.3 < r < 0.3 = **Medium Effect**
  -0.5 < r < 0.5 = **Large Effect**

## Converting pearson's Correlation Coefficient to z-score & probability
  As *r* is not normally distributed, we convert it to a normal distribution as
  \[
    z_r = \frac{1}{2}log_e(\frac{1+r}{1-r})\\

    SE_{z_r} = \frac{1}{\sqrt{N-3}}
  \]
  So it follows that the z-score of the correlation is
  \[
    z = \frac{z_r}{SE_{z_r}}
  \]

  Although the hypothesis that correlation is different than 0 is tested using t-statistic with N-2 degrees of freedom and give by
  \[
    t_r = \frac{r\sqrt{N-2}}{\sqrt{1-r^2}}
  \]

## Correlation methods in R
  Requires the data to be numeric. (Pearson's requires it to be interval.)
  * cor
  * cor.test
  * rcorr

## Pearson's correlation Coefficient
  assumptions
  * Requires data to be interval to be accurate measure of correlation
  * For statistical significance
    Variables need to be normally distributed.
    Exception: One of the variable is categorical with only two categories.

  ### Coefficient of determination (R^2)
    Measure of variability of one variable that is shared by another.

## Spearman's correlation Coefficient ($\rho$)
  Used when the data violates parametric assumptions such as non-normally distributed data
  Works by first ranking the data and then applying Pearson's equation

## Kendall's correlation Coefficient ($\tau$)
  For Non-parametric data
  Better estimate than Spearman's and should be used when small dataset and large number of tied ranks

## Partial correlation
  A correlation between two variables in which the effects of other variables are held constant is known as a partial correlation.
  >`pcor` calculates partial correlation
  >`pcor.test` calculates the significance.

## Part/Semi correlation
  Semi-partial correlation: a measure of the relationship between two variables while ‘controlling’ the effect that one or more additional variables has on one of those variables. If we call our variables x and y, it gives us a measure of the variance in y that x alone shares.
