#Testing assumptions

### Parametic data
Assumptions:
* Normally Distributed Data:
  Sampling Distribution is normally Distributed
  Central Limit Theorm:
    if sample data is approx normal, sampling distribution is normal
    large samples sizes yield sampling distribution that are normal.

  Check for normality
    Visually:
      * Histogram,
      * Quantile(Q-Q) plot
    Quantitative
      * Descriptive statistics
      * Shapiro-Wilk test
        Null hypothesis: Distribution same as normal
        If significant p value indicates non-normal distribution
        `shapiro.test(variable)`


* Homogeneity of variance:
  * variances should be the same throughout the data
  * In designs in which you test several groups of participants this assumption means that each of these samples comes from populations with the same variance
  * In correlational designs, this assumption means that the variance of one variable should be stable at all levels of the other variable

  Check for HoV:
    * Levene's test
      H_0: variances for the groups are equal
      Significant p value indicates, unequal variance
    * Hartley's F_max (Variance Ratio)
      Levene's is often significant for large data
      Hartley's F_max  is ratio between group with largest and smallest variance


* Interval data

* Independence
the behaviour of one participant does not influence the behaviour of another.


## Power Transformations



## Note
_Q-Q Plot_: Quantile-Quantile plot. Plots the data against another distribution (say normal distribution)
