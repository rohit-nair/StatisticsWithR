## Multiple Regression

### Sum of squares $R$ and $R^2$
$SS_T$ still represents difference between observed variable and mean value of outcome variable
$SS_R$ still represents the difference between value of $y$ predicted by model and observed value.
$SS_M$ Represents the improvement in prediction by using regression instead of mean. Shows the reduction in inaccuracy resulting from fitting the regression model to the data.

#### Multiple $R^2$.
Since there are multiple predictors, we can't look at simple $R^2$. Instead we look at **Multiple $R^2$**. Multiple $R^2$ is the square of correlation between observed value of y and the value of y predicted by the multiple regression. Hence **large value of $R^2$** represents **large correlation** between observed value and predicted value of outcome. Hence it's a gauge of how well the model predicted the observed value.

#### Parsimony-adjusted measure of fit.
Issue with $R^2$ is it will always go up with more variables to the model. Hence **model with more predictors will appear to fit better**.

#### Akiaike information criterion (AIC)
AIC penalizes a model for having more variables.
> *Larger AIC implies worse fit.*

\[
AIC = nln(\frac{SSE}{n}) + 2k
\]
n: number of cases in the model,
ln: natural log,
SSE: sum of square errors for the model,
k: number of predictor variables.

If a variable is added to the model (and if it doesn't improve the fit), $R^2$ still goes up and hence SSE would be reduced. But k will be reduced and hence the overall AIC will be higher.

**Limitations**
* No scale other than higher is worse and lower implies better fit,
* Can only be used to compare models of the same data as AIC of its own doesn't mean anything,

### Bayesian information criterion (BIC)
Another option to measure the fit of a model.


### Methods of regression
**How to select your variables**
* Ideally, predictors should be selected based on past research,
* If new variables should be added based on substantial theoretical importance.
* **Never** select hundreds of random predictors and bung them in model and hope it works.

**Order in which to add the variables**
If predictors are all uncorrelated then order doesn't effect parameters selection but that's highly unlikely in real world.
* **Hierarchical**
Based on past work and experimenter's decision
  * Predictors from past work are added first in the order of importance of predicting the outcome,
  * After that new predictors can be added
      1. All in one go,
      2. Stepwise,
      3. Hierarchical (most important predictors added first)

* ** Forced entry
  * All predictors with good theoretical reasoning are added simultaneously,
  * Experimenter makes no decision regarding order of predictors,
  * Some believe appropriate method for theory testing as stepwise method influenced by random variation in data and seldom replicable

* **Stepwise Methods**
  * Generally frowned upon by statisticians
  * $R$ cannot do automated stepwise regression
  * Forward method:
    1. Initial model is defined that contains only constant,
    2. Algo searches for a predictor that best predicts the outcome variable (highest correlation),
    3. Predictor is added to model and if it improves the ability of model to predict then the predictor is retained,
    4. Second predictor is selected based on highest semi-partial correlation.

  * Backward method:
    1. Opposite of forward method, in that all the parameters are added,
    2. Check for AIC going down when the parameter is removed,
    3. Repeat until removing causes AIC to go up.

  * Both method:
    1. Starts as forward method,
    2. Every time a variable is added, a removal test is performed for the least useful predictor.

  Of the forward and backward methods, backward is preferred due to **suppressor effect**: which occurs when a predictor has an effect when another predictor is held constant. Forward selection is more likely to remove parameter having suppressor effect. ie. the forward method runs the risk of making Type I error.

* **All-subset method**
  * Addresses the limitations of stepwise method which is it assesses the fit of the variable based on other variables already included in the model.
  * Does this by trying every combination of the variables to see which gives the best fit (determined by Mallow's $C_p$)
  * Drawback: number of combinations grows exponentially.

#### Choosing model
  * Stepwise method best avoided except for exploratory model building as
    1. It takes all the decisions away from the researcher,
    2. Based on partial correlation and hence could contrast with theoretical importance,
    3. Prone to overfitting and underfitting.

_____

### Accessing regression models
* Diagnostics: How well the model fits the data,
* Generalization: How well the model fits other samples
### Diagnostics

#### Outliers and Residuals
**Outliers**:
Is a case that differs from the main trend of the data causing our model to biased as it affects the regression coefficients (changing gradient and intercepts).
*Detecting outliers*
Outliers can be detected by using the difference between the value of outcome predicted by the model and the values of the outcome observed in the sample also known as *Residual*. If the model fits the sample poorly then the residuals will be large. Unstandardized residuals mentioned above are measured in the same units of outcome variable and hence are difficult to interpret across different models.

***Standardized Residuals (z-scores)*** calculated as residuals divided by the estimate of the standard deviation, overcomes this issue. We can use the properties of z-scores to this to determine values not explained by chance alone.
Some guidelines:
* if standardized residuals > 3.29 (~ 3), cause for concern as in an average sample a value this high cannot happen by chance alone.
* if more than 1% of sample cases have standardized residuals > 2.58 (~ 2.5) then there is evidence that level of error is unacceptable.
* if more than 5% of cases have standardized residuals > 1.96 (~2) then there is evidence that the model is poor representation of the data.

#### Influential cases
**Adjusted predicted value**
A case is removed from the sample and a model is generated. Using this model, the value for the outcome variable is calculated for this case called the Adjusted Predicted Value. If the case doesn't exert influence then the difference between Adjusted Predicted Value and original predicted value, known as **DFFit** will be zero.

**DFBeta**
The difference between a parameter estimated using all cases and estimated when one case is excluded is known as the DFBeta in R. DFBeta is calculated for every case and for each of the parameters in the model. By looking at the values of DFBeta, it is possible to identify cases that have a large influence on the parameters of the regression model.

**Studentized Residuals**
When difference between Adjusted Predicted Value and Observed Value (residual) is divided by the standard error it gives a standardized value known as Studentized Residual. This value can be compared across different regression analysis because it is measured in standard units and follows Student's t-distribution
It's useful to assess the influence of the case on the ability of the model to predict that case. But **doesn't provide information on how the case influences the model on the whole**.


**Cook's distance**
Cook's distance considers the effect of the case on the model. Values > 1 are causes for concern.

**Hat values (leverage)**
Gauges the influence of the observed value of the outcome variable over the predicted variable.
\[
Average \space Leverage = \frac{n+1}{k}
\]
where
$k$: number of predictors
$n$: number of participants
Leverage value of 0 indicates the case has no influence while a value of 1 indicates the case has complete influence. If no case exerts undue influence then we would expect the leverage values to be close to the average value $\frac{k+1}{n}$
Recommended cut-off value is $3\frac{k+1}{n}$.
Cases with large leverage value will not have large influence on the regression coefficients as they are measured on the outcome variable and not on the predictor variables.

***Note***
Diagnostics are tools that enable you to see how good or bad your model is in terms of fitting the sampled data. They are a way of assessing your model. They are not, however, a way of justifying the removal of data points to effect some desirable change in the regression parameters.

If a point is a significant outlier on Y, but its Cook’s distance is < 1, there is no real need to delete that point since it does not have a large effect on the regression analysis. However, one should still be interested in studying such points further to understand why they did not fit the model.



### Generalization
For a regression model to be generalize we must be sure that the underlining assumptions have been met and to see whether the model can generalize we can look at cross-validating it.

####Checking Assumptions
1. **Variable Types**
  Predictors: Quantitative or Categorical (with two categories)
  Outcome: Quantitative, continuous and unbounded
2. **Non-zero variance**
  Predictors should have non-zero variance
3. **No perfect multi-collinearity**
  No perfect linear relationship between two or more predictors. Predictors shouldn't be correlated too highly
4. **Predictors are uncorrelated with external variables**
  External variables are those that haven't been included in the model which influence the outcome variable. ie. no external variable that correlate with the variables included in the model.
5. **Homoscedasticity**
  At each level of the predictor variable the variance of the residual term should be constant.
6. **Independent errors**
  For any two observations the residuals should be uncorrelated. This is sometime referred to as lack of auto-correlation.
  > Test: Dublin-watson test
  Value ranges from 0-4  
  Value = 2 indicating that the residuals are uncorrelated.
  Value > 2 indicates that the residuals are negatively correlated
  Values < 2 indicate that the residuals are positively correlated.
  1 < Values > 3 are causes for concern.
  Note:
  Size of the statistics depends on predictors in the model and number of observations.
  Be careful! Depends on the order of the data.

7. **Normally Distributed Residuals (Errors)**
  It is assumed that the residuals in the model are normally distributed with a mean of 0. **Not to be confused** with predictors being normally distributed which is not a requirement.
8. **Independence**
  Values of the outcome variable are independent ie each value of the outcome variable comes from a separate entity.
9. **Linearity**
  The mean value of the outcome variable for each increment of the predictor lies in a straight line; ie. the relationship we are modelling is linear.

Note:
When the assumptions are met the model can be applied to the population of interest; ie. the coefficients and parameters for the regression equations are said to be **unbiased**.
This doesn't mean the model is identical to population model but instead ***on average*** the regression model is same as the population model.

#### Cross-validation
Assesesing the accuracy of the model across differnt samples is known as cross-validating. If there is significant drop in the predictive power of the model when applied to a different sample then the model clearly doesn't generalize. Methods of cross-validating:
1. Adjusted $R^2$
Adjusted $R^2$ indicates the loss of predictive power or **shrinkage**. The adjusted value tells us how much variance in Y would be accounted for if the model had been derived from the population from which the sample was taken.
Stein's formula:
\[
Adjusted \space R^2 = 1- [(\frac{n-1}{n-k-1})(\frac{n-2}{n-k-2})(\frac{n+1}{n})](1-R^2)
\]
where:
$R^2$ is the unajusted value,
k is number of predictors,
n is number of participants

2. Data Splitting
Split your data and run regression models and compare.

#### Sample size in Regression
According to Greens (1991), if you want to test the model overall, then
\[
Minimum \space Sample \space Size = 50 + 8k
\]
where k is the number of predictors.

If you want to test individual predictors, then
\[
Minimum \space Sample \space Size = 104 + k
\]

If interested in both then use the larger of two.

But Sample Size required actually depends on the **size of the effect** (i.e., how well our predictors predict the outcome) and how much **statistical power** we want to detect these effects.
1. If you expect to find a large effect then a sample size of 80 will always suffice (with up to 20 predictors) and if there are fewer predictors then you can afford to have a smaller sample;  
2. If you’re expecting a medium effect, then a sample size of 200 will always suffice (up to 20 predictors), you should always have a sample size above 60, and with six or fewer predictors you’ll be fine with a sample of 100; and
3. If you’re expecting a small effect size then just don’t bother unless you have the time and resources to collect at least 600 cases of data (and many more if you have six or more predictors).


#### Multi-collinearity
**Multi-collinearity** exists when there is  strong correlation between two or more predictors in a regression. **Perfect collinearity** exists when one predictor is a perfect linear combination of the other. Issue with collinearity is that it becomes impossible to obtain unique combination of regression coefficients because there are a infinite number of combination of coefficients that would work equally well. ***Multi-collinearity is virtually unavoidable.***
**Issues with Multi-collinearity**
* Untrustworthy bs
As collinearity increases, so does the standard error for the $b$ coefficients. ie. $b$ are more variable across samples due to which the predictor variables will be unstable across samples.
* Limit the size of $R$
$R$ is the measure of the multiple correlation between the predictors and the outcome, while $R^2$ represents the variance in the outcome for which the predictor accounts. Hence addition of a second correlated predictor will not affect $R$ significantly as part of the variance that this predictor accounts for is already accounted for by the first predictor. Hence having uncorrelated predictors is beneficial.
* Relative importance of predictors
If multicollinearity is present then each predictor accounts for similar variance in outcome hence it becomes difficult to determine which predictor is important. The model could include either one interchangeably.

**Diagnosing multicollinearity**
* Correlation matrix
One way to identify multicollinearity is to scan the correlation matrix and see whether any correlates very highly (ie. correlation > 0.8). Good ball park method but misses subtle forms of multicollinearity.
* Variable inflation factor (**VIF**)
VIF indicates whether a predictor has strong linear relationship with the other predictors.
VIF > 10 || AVG(VIF) > 1 are causes for concern as multicollinearity could be biasing the regression model.
Another related statistic is ***tolerance*** which is reciprocal of VIF (1/VIF). Values < 0.2 are causes for concern.
**$R$ could generate VIF and other correlation diagnostics.**

### Strategy for running regression
Measure predictor variables for which there is sound theoretical reasons for predicting the outcome. Run regression analysis in which all the predictors are entered in the model and examine output to see which predictors contribute substantially to predict the outcome. Rerun the analysis including only the important predictors and use the resulting parameter estimates to define the regression model.

### Command
> .~. means keep the outcome and predictor the same, where . means keep the same.

Ex: model2 <- lm(model1, .~. + newPredictor1 + newPredictor2)
