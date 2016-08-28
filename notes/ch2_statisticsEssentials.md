### Essentials of Statistics

#### Population vs Sample
  * Population: in statistical terms this usually refers to the collection of units (be they people, plankton, plants, cities, suicidal authors, etc.) to which we want to generalize a set of findings or a statistical model.

  * Sample: small subset of the population used to infer things about the population as a whole. The bigger the sample, the more likely it is to reflect the whole population. If we take several random samples from the population, each of these samples will give us slightly different results. However, on average, large samples should be fairly similar.


#### Statistical Models
  * **Mean:** $R$

  * **Deviance:** Difference between observed data and our model; thought as the error in our model.
  \[
    Deviance = X - \bar{X}\\
    \sum{Deviance} = \sum{X-\bar{X}} = 0
  \]

  * **Sum of squared errors (SS):** Aggregate of all errors; Squared so that the +ve and -ve don't cancel out. Not a good representation of sample as is dependent on amount of data.
  \[
    SS = \sum{(X - \bar{X})^2}
  \]

  * **Variance:** Average error between mean and observation. error in the sample as a representation of error in population. Since we are interested in population we devide by $N-1$ (degree of freedom) instead of $N$.
  \[
    Variance = \frac{\sum(X - \bar{X})^2}{N - 1}
  \]

  * **Degrees of freedom:** Essentially it is the number of ‘entities’ that are free to vary when estimating some kind of statistical parameter. In a more practical sense, it has a bearing on significance tests for many commonly used test statistics (such as the F-ratio, t-test, chi-square statistic) and determines the exact form of the probability distribution for these test statistics.

  * **Standard Deviation:** The average error between mean and observation as an unit of observation.
  \[
    Standard Deviation = s = \sqrt{\frac{\sum(X - \bar{X})^2}{N - 1}}
  \]
  &ensp;&ensp;&ensp;&ensp;*Kurtosis:* The sharpness of the peak of a frequency-distribution curve.
  &ensp;&ensp;&ensp;&ensp;*Platykurtic:* Large standard deviation which results in large dispersion and flatter curve.
  &ensp;&ensp;&ensp;&ensp;*Leptokurtic:* Small standard deviation which results in observations being closer together and spikier curve.

  * **Sampling Variation:** Variation in the mean of different samples drawn from the same population.

  * **Sampling Distribution:** Frequency distribution of sample means from the same population.


#### Central Limit Theorm
This theorem states that when samples are large (above about 30) the sampling distribution will take the shape of a normal distribution regardless of the shape of the population from which the sample was drawn. For small samples the $t-distribution$ better approximates the shape of the sampling distribution. We also know from this theorem that the standard deviation of the sampling distribution (i.e., the standard error of the sample mean) will be equal to the standard deviation of the sample ($s$) divided by the square root of the sample size ($N$).


#### Standard Error
The standard deviation of the sample means. It represents how well the sample mean represents the population mean.

  \[
    Standard Error = \sigma_x = \frac{s}{\sqrt{N}}
  \]


#### Confidence Intervals
For a given statistic calculated for a sample of observations (e.g., the mean), the confidence interval is a range of values around that statistic that are believed to contain, with a certain probability (e.g., 95%), the true value of that statistic (i.e., the population value).

* For large samples use $z-scores$
\[
  Lower Boundary = \bar{X} - (1.96 * SE)\\
  Upper Boundary = \bar{X} + (1.96 * SE)\\
  z-score_p = Z_\frac{1-p}{2}
\]
&ensp;&ensp;&ensp;&ensp;$Z-score$ for 95% confidence = $Z_\frac{1-0.95}{2}$ = $Z_{0.025}$ = $1.96$

* For small samples the sampling distribution is not normal, it has $t$ distribution. $t$-distribution is family of probability distribution which changes shape as sample grows. So instead of $z-scores$ we use value of $t$.
\[
  Lower Boundary = \bar{X} - (t_{n-1} * SE)
  Upper Boundary = \bar{X} + (t_{n-1} * SE)
\]
  For a 95% confidence interval we find the value of t for a two-tailed test with probability of .05, for the appropriate degrees of freedom.
