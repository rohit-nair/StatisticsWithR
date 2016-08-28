## Logistic Regression

Logistic regression helps us to predict outcomes that are categorical variables from predictor variables that are continuous or categorical. When predicting membership of only two categorical outocmes the analysis is known as ***binary logistic regresion***, but when predicting membership to more than two categories we use ***multinomial (or polychotomous) logistic regression***.

### Principles
Similar to linear regression
\[
Y_i = b_0 + b_1X_1 + \epsilon_i
\]
but in logistic regression instead of predicting the value of variable $Y$ from a predictor variable $X_i$ or several predictors($X_s$), we predict the ***probability of $Y$ occurring*** given known values of $X_1$ (or $X_s$).
\[
P(Y) = \frac{1}{1 + e^{-(b_o + b_1X_{1i})}}
\]
The reason linear regression cannot be applied when the outcome variable is categorical is because one of the assumption of linear regression is that the relationship between variables is linear. This issue is overcome by taking the logarithmic transform. This logarithmic term is called ***logit***. The values for the parameters are estimated using the ***maximum-likelihood estimation***, which selects coefficients that make the observed value most likely to have occurred.

### Assessing the model
#### log-likelihood statistic
Similar to linear regression where we used Pearson' Correlation ($R^2$) to assess whether a model fits the data, in Logistic Regression we use ***log-likelihood***.
\[
log-likelihood = \sum_{i=1}^{N}{[Y_iln(P(Y_i)) + (1-Y_i)ln(1-P(Y_i))]}
\]
which is based on summing the probability associated with the predicted and actual outcomes. It indicates how much unexplained information there is after the model has been fitted. ***Larger the value of log-likelihood, the more unexplained observations there are***.

#### Deviance statistic
Deviance is calculated as
\[
deviance = -1 * log-likelihood
\]
and is referred to as $-2LL$. It is more convenient to use deviance as it has a ***Chi-squared distribution*** making it easy to calculate significance of the value against a ***baseline which in logistic regression is the outcome that occurs most often*** or when only a constant is included.

\[
\chi^2 = (-2LL(baseline))-(-2LL(new)) \\
       = 2LL(new) - 2LL(baseline) \\

df = k_{new} - k_{baseline}
\]

#### $R$ and $R^2$
$R$-statistic is the partial correlation between the outcome variable and each of the predictor variables, and it ***varies between -1 and 1***. Positive value indicates as the predictor variable increases so does the likelihood of the event occurring.

\[
R = \sqrt\frac{z^2 - 2df}{-2LL(baseline)}
\]
where $z^2$is the Wald statistic,
$-2LL$ is the deviance from baseline model.
Due to its dependence on Wald statistic, ***R-statistic is not an accurate measure*** and is invalid to square this value and interpret it as in Linear Regression.
Hence other $R^2$ has been suggested that would be good analogous to Linear Regression $R^2$.
Hosmer and Lemeshow:
\[
R_L^2 = \frac{-2LL(model)}{-2LL(baseline)}
\]
Cox and Snell's
\[
R_{CS}^2 = 1-exp(-\frac{(-2LL(new))-(-2LL(baseline))}{n})
\]
Nagelkerke
\[
R_{N}^2 = \frac{R_{cs}^2}{1-exp(-\frac{((-2LL(baseline))}{n})}
\]

#### Information Criteria
Akaike Information Criterion(AIC) and Bayes Information Criterion (BIC) are used to solve the problem with $R^2$: that everytime a variable is added to the model, $R^2$ increases. So IC penalizes a model that contains more predictors.
\[
AIC = -2LL + 2k
\]
BIC is similar to AIC but adjusts the penalty included in the AIC (2k term) by the number of cases.
\[
BIC = -2LL + 2k * log(n)
\]
where n is the number of cases in the model.

#### z-statistic
Like the t-statistic in linear regression, the z-statistic tells us whether the b coefficients for that predictor is significantly different from zero. If coefficient is significantly different from 0, it means that predictor is making a significant contribution to the prediction of the outcome.
\[
z = \frac{b}{SE_b}
\]
Probably its more accurate to use the likelihood ratio statistic. The reason for using z-statistic ***cautiously*** is because when regression coefficient (b) is large, the standard error tends to be come inflated resulting in z-statistic being underestimated.
The inflation of the standard error increases the probability of rejecting a predictor as being significant when in reality its making a significant contribution to the model (Type II error). z-statistic is also known as ***Wald Statistic***.

#### Odds ratio
Odds ratio indicates the change in odds resulting from a unit change in the predictor. Similar to b coefficient but easier to understand as it doesn't require logarithmic transformation.
\[
odds = \frac{P(event \space occurring)}{P(event \space not \space occurring)} \\
P(event Y) = \frac{1}{1 + e^{-(b_0+b_1X_1i)}} \\
P(no event Y) = 1-P(event Y)  \\
  \\
\delta odds = \frac{odds \space after \space unit \space change \space in \space predictor}{original \space odds}
\]
$\delta odds$ is the ***Odds Ratio*** which we can use to interpret it as change in odds. If odds ratio is > 1, it indicates that as the predictor increases, the odds of the outcome occurring increases.


### Methods of regression

Forced entry is the ***default method*** in which predictors are placed into the regression model in one block, and estimate parameters for each predictor.

Stepwise method begins with a model that includes only a constant and then adds single predictors to the model based on the criterion that adding the variable must improve the AIC or BIC (whichever you chose). The computer proceeds until none of the remaining predictors have decreased the criterion.

In backward method the computer begins the model with all predictors included and then tests whether any of these predictors can be removed from the model without increasing the information criterion. If it can, it is removed from the model, and the variables are all tested again.

The better of the two approach is the backward approach due to ***suppressor effect*** (ref linear regression, predictors have significant effect but only when other variables are held constant) hybrid approach. Hence forward method runs higher risk of Type II error. But overall the hybrid approach is better.

#### Selecting a regression method:
Main consideration is whether you are testing a theory or merely carrying out exploratory work. Some consider stepwise have no value for theory testing.

Stepwise is ok when used in situation where causality is not of interest and you merely wish to find a model to fit your data.


### Assumptions
1. Linearity
The linearity assumption in logistic regression, therefore, is that there is a linear relationship between any continuous predictors and the ***logit*** of the outcome variable. This assumption can be tested by looking at whether the interaction term between the predictor and its log transformation is significant.

2. Independence of errors
Basically it means that cases of data should not be related; for example, you cannot measure the same people at different points in time (well, you can actually, but then you have to use a multilevel model”.

3. Multicollinearity
Predictors should not be too highly correlated. As with ordinary regression, this assumption can be checked with tolerance and VIF statistics, the eigenvalues of the scaled, uncentred cross-products matrix, the condition indices and the variance proportions.

### Problems in logistic regression

R solves logistic regression by an iterative method trying to converge (i.e., at each new attempt the ‘approximations’ of parameters are the same or very similar to the previous attempt). Sometimes it cannot converge and give a result with ***large standard*** errors. Two situations can cause this: incomplete information and complete separation.

#### Incomplete information
Incomplete information happens when the data is not sufficient enough to make a conclusion. This happens for both categorical and continious variables. This should be checked before you run the analysis using a ***crosstabulation*** table. While you’re checking these tables, you should also look at the expected frequencies in each cell of the table to make sure that they are ***greater than 1 and no more than 20% are less than 5***. This is because the goodness-of-fit tests in logistic regression make this assumption. As a general point, whenever samples are broken down into categories and one or more combinations are empty it creates problems. These will probably be signalled by coefficients that have unreasonably large standard errors.

#### Complete separation
A situation in logistic regression when the outcome variable can be perfectly predicted by one predictor or a combination of predictors. This prevents the algorithm from converging because there is no data point in the middle where the curve slopes. The lack of data means that R will be uncertain about how steep it should make the intermediate slope and it will try to bring the centre as close to vertical as possible, but its estimates veer unsteadily towards infinity (hence large standard errors). This problem often arises when too many variables are fitted to too few cases. Often the only satisfactory solution is to collect more data, but sometimes a neat answer is found by using a simpler model.
