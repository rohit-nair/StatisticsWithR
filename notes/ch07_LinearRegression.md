## Ordinary Least Squared Regression (OLS Regression)

### Residuals:
The difference between the line (model) and the actual data. We calculate the vertical distance as we want to find how well x predicts y. In regression this is called residuals rather than deviation.

### Sum of squares, $R$ and $R^2$

#### Total sum of squares ($SS_T$)
Sum of square of difference between the values and the mean.

\[
SS_T = \sum{(y - \bar{y})^2}
\]

#### Residual Sum of Squares ($SS_R$)
Sum of square of residuals.
\[
SS_R = \sum{(observed - model)^2}
\]

#### Model Sum of Squares
Represents the improvement in prediction by using regression instead of mean. Shows the reduction in inaccuracy resulting from fitting the regression model to the data.
\[
SS_M = \sum{SS_T - SS_R}
\]

#### $R^2$
$R^2$ represents the amount of variance in the outcome explained by the model ($SS_M$) relative to how much variance there was to explain the first place ($SS_T$). As a percentage it represents the percentage of the variation of the outcome explained by the model.
\[
R^2 = \frac{SS_M}{SS_T}
\]

#### R
In simple regression the square root of $R^2$ gives the Pearson's Correlation Coefficient.
\[
Pearson's \space Corrrelation \space Coefficient (R) = \sqrt{R^2}
\]

Hence, $R$ gives a good estimate of the overall fit of the model while $R^2$ provides a good gauge of substantive size of relationship.

#### F-ratio
F-ratio is usually the ratio between the systematic variance divided by amount of unsystematic variance or in other words, model compared with error in the model.

\[
F-ratio = \frac{MS_M}{MS_R} \\
where, \\
MS_M = \frac{MS}{DF_M} \\
MS_R = \frac{MS}{DF_R}
\]
$DF_M$ = Number of variables in the model,
$DF_R$ = Number of observations minus number of parameters being estimated; in other words number of beta coefficients including the constants.

For a good model, **F-ratio > 1 (atleast)** as improvements in prediction ($MS_M$) to be large and difference between model and observed data to be small ($MS_R$).
The exact magnitude of this F-ratio can be assessed using critical values for the corresponding degrees of freedom.

#### Assessing individual predictors
If a variable significantly predicts an outcome, it's b-value will be significantly different from 0. We test the significance of b-value using the **t-statistic** where the null hypothesis is that b is 0.

**Testing significance of $b$**
Significance of $b$ is calculated using t-test. Algo:
1. Lots of samples are taken,
2. A model is created for each and the b-value is calculated,
3. A histogram is created for the b-value to understand it's variance
4. SE is calculated using SD. If SE is small it means most samples are likely to have b values similar to our sample

$t-test$ tells us the b-value is different from 0 relative to b-values across sample.
If SE is small a small change in b from 0 can represent a meaningful difference.
\[
t = \frac{b_observed}{SE_b}
\]

In regression, degrees of freedom is defined as
\[
df = N-p-1
\]
where,
N = total sample size,
p = number of predictors

### Calculating regression

    newModel <- lm(outcome ~ predictor(s), data = data.frame, na.action = an action)

  ~ represents "predicted from"
