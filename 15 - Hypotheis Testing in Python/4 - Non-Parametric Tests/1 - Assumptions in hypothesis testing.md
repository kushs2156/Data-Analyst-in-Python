Each hypothesis test we've seen so far makes assumptions about the data. It's only when these assumptions are met that it is appropriate to use that hypothesis test.
## Randomness
Whether it uses one or multiple samples, every hypothesis test assumes that each sample is randomly sourced from its population. If we don't have a random sample, then it won't be representative of the population. To check this assumption, we need to know where our data came from. There are no statistical or coding tests we can perform to check this. If in doubt, ask the people involved in data collection, or a domain expert that understands the population being sampled.
## Independence of observations
Tests also assume that each observation is independent. There are some special cases like paired t-tests where dependencies between two samples are allowed, but these change the calculations, so we need to understand where such dependencies occur. As we saw with the paired t-test, not accounting for dependencies results in an increased chance of false negative and false positive errors. Not accounting for dependencies is a difficult problem to diagnose during analysis. Ideally, it needs to be discussed before data collection.
## Large sample size
Hypothesis tests also assume that our sample is large enough that the Central Limit Theorem applies, and the sample distribution can be assumed to be normally distributed. Smaller samples incur greater uncertainty, which may mean that the Central Limit Theorem does not apply and the sampling distribution might not be normally distributed. The increased uncertainty of a small sample means we get wider confidence intervals on the parameter we are trying to estimate. If the Central Limit Theorem does not apply, the calculations on the sample, and any conclusions drawn from them, could be nonsense, which increases the chance of false negative and false positive errors. How big our sample needs to be to be "big enough" depends on the test.
## Large sample size: t-test
For one sample t-tests, a popular heuristic is that we need at least 30 observations in our sample. For the two sample case or ANOVA, we need 30 observations from each group. That means we can't compensate for one minority group sample by making the majority group bigger. In the paired case, we need 30 pairs of observations. Sometimes we can get away with less than 30 in each of these tests; the important thing is that the null distribution appears normal. This is often the case at around 30 and that's the reason for this somewhat arbitrary threshold.

| One sample                      | Two samples                                                       | Paired samples                                                                                        | ANOVA                                                                                    |
| ------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| $n \geq 30$<br>$n$: sample size | $n_1 \geq 30, n_2 \geq 30$<br>$n_i$: sample size for<br>group $i$ | At least 30 pairs of<br>observations across<br>the samples<br>Number of rows<br>in our data $\geq 30$ | At least 30 <br>observations in<br>each sample<br>$n_i \geq 30$ for all<br>values of $i$ |
## Large sample size: proportion tests
For one sample proportion tests, the sample is considered big enough if it contains at least 10 successes and 10 failures. Notice that if the probability of success is close to zero or close to one, then we need a bigger sample. In the two sample case, we require 10 successes and 10 failures from each sample.

| One sample                                                                                       | Two samples                                                                                                                                         |
| ------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| Number of successes in sample is<br>greater than or equal to 10<br>$n \times \hat{p} \geq 10$    | Number of success in each sample is<br>greater than or equal to 10<br>$n_1 \times \hat{p}_1 \geq 10$<br>$n_2 \times \hat{p}_2 \geq 10$              |
| Number of failures in sample is<br>greater than or equal to 10<br>$n \times (1-\hat{p}) \geq 10$ | Number of failures in each sample is<br>greater than or equal to 10<br>$n_1 \times (1 - \hat{p}_1) \geq 10$<br>$n_2 \times (1 - \hat{p}_2) \geq 10$ |
- $n$: sample size
- $\hat{p}$: proportion of successes in sample
## Large sample size: chi-square tests
The chi-square test is slightly more forgiving and only requires 5 successes and 5 failures in each group, rather than 10.

|                                                                                                                                        |
| -------------------------------------------------------------------------------------------------------------------------------------- |
| The number of successes in each group is greater than or equal to 5<br>$n_i \times \hat{p}_i \geq 5 \text{ for all values of } i$      |
| The number of failures in each group is greater than or equal to 5<br>$n_i \times (1 - \hat{p}_i) \geq 5 \text{ for all values of } i$ |
- $n_i$: sample size for group $i$
- $\hat{p}_i$: proportion of successes in sample group $i$
## Sanity check
One more check we can perform is to calculate a bootstrap distribution and visualise it with a histogram. If we don't see a bell-shaped normal curve, then one of the assumptions hasn't been met. In that case, we should revisit the data collection process, and see if any of the three assumptions of randomness, independence, and sample size do not hold.
## Let's practice!
Time to check some assumptions!