## Non-parametric tests
* Sometimes known as assumption-free tests as they make fewer assumptions,
* Generally based on ranking,
* Less powerful as it uses ranks and hence loses some info in the process,
* Examples:
  Wilcoxon rank-sum test (also called Mann-Whitney test)
  Wilcoxon signed-rank test
  Friedman's test
  Kruskal-Wallis test

### Independent Non-Parametric Tests
#### Wilcoxon rank-sum test
  Algo:
  1. Rank the data ignoring which group it belongs to
  2. In case of tie, find the potential rank (Average of the ranks)
  3. Find mean rank, which is just sum of number of elements in group
  \[
r_m = \frac{N(N+1)}{2}
  \]
  4. Subtract mean rank ($r_m$) from the sum of group wise ranks to get the statistic
  5. Calculate the p-value for the statistic using either
      1. Monte Carlo Method
      2. Normal approximation with continuity correction
        Doesn't assumes data is normal but instead assumes sampling distribution of W statistic is normal.
        Does continuity correction as the rank is ordinal and not interval.

  **Function in $R$**

      wilcox.text

  **Effect size**
  The function doesn't calculate effect size, so we do it using
  \[
  r = \frac{z}{\sqrt{N}} \\
  where, z = qnorm($p.value/2)
  \]
  where, $N$ is number of **observations** and not number of **subjects**.

  **Reporting Results**
  >Depression levels in ecstasy users (Mdn = 17.50) did not differ significantly from alcohol users (Mdn = 16.00) the day after the drugs were taken, W = 35.5, p = 0.286, r = –.25. However, by Wednesday, ecstasy users (Mdn = 33.50) were significantly more depressed than alcohol users (Mdn = 7.50), W = 4, p < .001, r = –.78.


### Dependent Parametric Tests
#### Wilcoxon signed-rank test
Algo:
1. Difference of two effects are calculated
2. The **absolute** difference are assigned potential ranks (ties are averaged)
3. Sum for positive ($T_+$) and negative ($T_\_$) ranks are calculated.
4. Mean test statistics ($\bar{T}$) is calculated as
\[
  \bar{T} = \frac{n(n+1)}{4}
\]
5. SE for test statistics ($SE_\bar{T}$) is calculated as
\[
SE_\bar{T} = \sqrt{\frac{n(n+1)(2n+1)}{24}}
\]
6. $z$-score is calculated using $\bar{T}$ & $SE_\bar{T}$ as
\[
z = \frac{X - \bar{X}}{s} = \frac{T-\bar{T}}{SE_\bar{T}}
\]
7. Calculate the $p$-value for the $z$

**Function in $R$**
Same function as Wilcoxon rank-sum test but with the argument *paired=TRUE*

    wilcox.test

_Note_
The function outputs a $V$ value and $p$-value. $V$ represents $T_+$ so a high $V$ value means there was a significant positive correlation.

**Reporting Results**
> For ecstasy users, depression levels were significantly higher on Wednesday (Mdn = 33.50) than on Sunday (Mdn = 17.50), p = .047, r = –.56. However, for alcohol users the opposite was true: depression levels were significantly lower on Wednesday (Mdn = 7.50) than on Sunday (Mdn = 16.0), p = .012, r = –.45.
