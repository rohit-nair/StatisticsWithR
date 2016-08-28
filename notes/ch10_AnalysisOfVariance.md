## Analysis of Variance (ANOVA)
* Used when comparing **more than 2** conditions,
* Cannot use $t$-test as if we do pair-wise tests, the $Type\space I$ error rate increases.
Example:
  If we have 5 conditions and we do pair-wise $t$-test, that's 10 experiments.
  As these experiments are independent, the collective probability of having no $Type\space I$ error is $(0.95)^10=0.6$. Hence the probability of $Type\space I$ error is $1-0.6 = 0.4$; ie. the probability of have $Type\space I$ error increased from the acceptable $0.05$ to $0.4$.
* Tests the *null hypothesis* that **all group means are equal**. (Similar to $t$-test which tests that two samples have same mean.)
* Is an **Omnibus** test, ie. it tests for overall effect and doesn't provide information on which group were di/ssimilar

### F-Statistics or F-ratio
\[
F-Statistics\space (F-Ratio)= \frac{systematic\space error}{Unsystematic\space error} = \frac{model}{error}
\]

### ANOVA as special case of regression
* Experimental researchers use regression while correlational researchers use ANOVA.
* Regression model is easier to understand when doing complex designs compared to variance-ratio method
* Variance-ratio method becomes unmanagable in special circumstances such as unequal sample sizes.
(R treats ANOVA in regressiony way, using General Linear Model (GLM))

### Basic ANOVA equation
All ANOVA equation boils down to the following basic equation:
\[
  deviation = \sum(observed - model)^2
\]
