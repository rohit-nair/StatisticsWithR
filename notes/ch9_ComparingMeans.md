## Comparing two means

### Median Split
  * Devil's Work
  * Converting continuous variable to *Dichotonomous* variable causes lose of information
  * Effect sizes get smaller: if you correlate two continuous variables then the effect size will be larger than if you correlate the same variables after one of them has been dichotomized. Effect sizes also get smaller in ANOVA and regression.
  * There is an increased chance of finding spurious effects.

  One of the rare situations in which dichotomizing a continuous variable is justified, according to MacCallum et al., is when there is a clear theoretical rationale for distinct categories of people based on a meaningful break point.

### t-test (Parametric test)
  Versatile test which can be used to test whether
  * correlation Coefficient is different from 0
  * regression Coefficient (b) is different from 0
  * two group means are different

  #### Independent-mean t-test
  This test is used when there are **two experimental conditions and different participants** were assigned to each condition (this is sometimes called the independent-measures or independent-samples t-test).

  #### Dependent-mean t-test
  This test is used when there are **two experimental conditions and the same participants** took part in both conditions of the experiment (this test is sometimes referred to as the matched-pairs or paired-samples t-test).


  #### _Assumptions_
  **Dependent t-test**
  * Sampling distribution (difference of scores, not the scores themselves) is normally distributed
  * Data is measured atleast at interval level.

  **Independent t-test**
  * Scores are normally distributed
  * Homoscedasticity: Homogeneity of variance (at least in theory)
    This is no longer relevant as it matters only for unequal group sizes for which the tests don't work. Further there is a Welch's t-test for correction when the assumption is violated. So it's better to just run the test which would correct if the assumption is violated and not if it wasn't.

### Independent t-test

  \[
  t = \frac{\delta Observed_{sampleMeans} - \delta Expected_{population means}}{SD_{EstimateDiffSampleMeans}} \\
  t = \frac{(\bar{X_1} - \bar{X_2})-(\bar{\mu_1} - \bar{\mu_2})}{SE_{estimate}}
  \]
  From null hypothesis
  \[
  (\bar{\mu_1} - \bar{\mu_2}) = 0
  \]
  **Variance sum theorm** states that variance of a difference between two independent variables is equal to the sum of their variances (see, for example, Howell, 2006)
  \[
  SE_{Pop1} = \frac{s_1}{\sqrt{N_1}} \\
  SE_{Pop1} = \frac{s_2}{\sqrt{N_2}}
  \]
  From which we get variances:
  \[
  var_{pop1} = \frac{{s_1}^2}{N_1} \\
  var_{pop1} = \frac{{s_2}^2}{N_2} \\

  var_{sampling dist of differences} = \frac{{s_1}^2}{N_1} + \frac{{s_2}^2}{N_2}
  \]

  SE sampling distribution of differences:
  \[
  SE_{diff} = \sqrt{\frac{{s_1}^2}{N_1} + \frac{{s_2}^2}{N_2}}
  \]

  Which implies,
  \[
  t = \frac{(\bar{X_1} - \bar{X_2})}{\sqrt{\frac{{s_1}^2}{N_1} + \frac{{s_2}^2}{N_2}}}
  \]
  This is valid only if sampling sizes are equal which usually is not the case. Hence a **pooled variance** is calculated as:
  \[
  s_p = \frac{(n_1 - 1){s_1}^2 + (n_2 - 1){s_2}^2}{n_1+n_2-2}
  \]
  where the standard deviations are weighted by the degrees of freedom.

  And hence
  \[
  t = \frac{(\bar{X_1} - \bar{X_2})}{\sqrt{\frac{{s_p}^2}{N_1} + \frac{{s_p}^2}{N_2}}}
  \]

  #### Effect Size
  \[
  r = \sqrt{\frac{t^2}{t^2 + df}}
  \]

### Dependent t-test

\[
  t-statistic = \frac{model}{error} = \frac{Systematic \space variation}{Unsystematic \space variation} \\
  t = \frac{\bar{D}-\mu_D}{\frac{s_D}{\sqrt{N}}}
\]
  $\bar{D}$: Avg difference, ie. on average a person's score differed between cond 1 & 2.

  #### Standard error of differences
  If we were to take several pairs of samples from a population and calculate their means, then we could also calculate the difference between their means. If we plotted these differences between sample means as a frequency distribution, we would have the sampling distribution of differences. The standard deviation of this sampling distribution is the standard error of differences. As such it is a measure of the variability of differences between sample means.

  #### Dependent t-test in R
  >*t.test(col1, col2, paired = TRUE)*

  **Robust method to compare dependent means**
  > *yuend(col1, col2, trim = 0.2, alpha = 0.5)*

  #### Effect Size
  \[
  r = \sqrt{\frac{t^2}{t^2 + df}}
  \]

### Between groups vs repeated measures
  Repeated-measures design (same participant are used for both conditions) has significantly **more power** compared to Between Groups (two groups are used for two conditions) as the former reduces the **Unsystematic Variance** (often called the error variance) making it easier to detect **Systematic Variance**.

  Hence data collection plays an important part in detecting a difference and not detecting a difference.
