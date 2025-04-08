In the previous lesson, we calculated the test statistic $t$. The test statistic, $t$, follows a t-distribution. t-distributions have a parameter called the degrees of freedom, or `df` for short. Here's a line plot of the PDF of a t-distribution with one degree of freedom, and the PDF of a normal distribution. Notice that the t-distribution for small degrees of freedom has fatter tails than the normal distribution, but otherwise they look similar.
![[Pasted image 20250317130227.png]]As we increase the degrees of freedom, the t-distribution gets closer to the normal distribution. In fact, a normal distribution is a t-distribution with infinite degrees of freedom. Degrees of freedom are defined as the maximum number of logically independent values in the data sample. That's a fairly tricky concept, so let's try an example.
## Calculating degrees of freedom
Suppose our dataset has 5 independent observations, and that four of the values are 2, 6, 8, and 5. Suppose we also know the sample mean is 5. With this knowledge, the fifth value is no longer independent; it must be 4. Even though all five observations in the sample were independent, because we know an additional fact about the sample - that is has a mean of 5 - we only have 4 degrees of freedom. In our two sample case, there are as many degrees of freedom as observations, minus two because we know two sample statistics, the means for each group.
$$
df = n_{child} + n_{adult} - 2
$$
## Hypotheses
Recall the hypotheses for our Stack Overflow question about compensation for the two age groups. Since this is a "greater than" alternative hypothesis, we need a right-tailed test.
## Significance level
We're going to calculate a p-value in a moment, but we first need to decide on a significance level. There are several possibilities; let's use $\alpha = 0.1$. That means that we reject the null hypothesis in favour of the alternative if the p-value is less-than-or-equal-to 0.1.
## Calculating p-values
In Chapter 1, to get the p-value, we transformed the z-score with the normal CDF. Since it was a right-tailed test, we subtracted the result from one. In the previous video, we used an approximation for the test statistic standard error using sample information. Using this approximation adds more uncertainty and that's why this is a t instead of a z problem. The t-distribution allows for more uncertainty when using multiple estimates in a single statistic calculation. Here, the multiple estimates correspond to the sample mean and the sample standard deviation.
- z-statistic: needed when using one sample statistic to estimate a population parameter
- t-statistic: needed when using multiple sample statistics to estimate a population parameter
## Calculating p-values: two means from different groups
Now we are calculating means rather than proportions, the z-score is replaced with a t test statistic. This is the value calculated in the previous video. The calculation also needs the degrees of freedom, which is the total number of observations in both groups, minus two.
```Python
numerator = xbar_child - xbar_adult
denomiator = np.sqrt(s_child ** 2 / n_child + s_adult ** 2 / n_adult)
t_stat = numerator / denomiator
>>1.86993133416221844
```
```Python
degrees_of_freedom = n_child + n_adult - 2
>>2259
```
To calculate the p-value, we need to transform the test statistic using the t-distribution CDF instead of the normal distribution CDF. Notice the use of `t.cdf` instead of `norm.cdf`, and that the df argument is set to the degrees of freedom. This p-value is less than the significance level of 0.1, so we should reject the null hypothesis in favour of the alternative hypothesis that Stack Overflow data scientists who started coding as children earn more.
```Python
from scipy.stats import t
1 - t.cdf(t_stat, df=degrees_of_freedom)
>>0.030811302165157595
```
## Let's practice!
While I re-evaluate my own childhood and wonder why I didn't start programming earlier, time for you to do some exercises.