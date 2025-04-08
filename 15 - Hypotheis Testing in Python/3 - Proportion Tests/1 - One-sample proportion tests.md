Let’s return to thinking about testing proportions, as we did in Chapter 1. The hypothesis tests in Chapter 1 measured whether or not an unknown population proportion was equal to some value. We used bootstrapping on the sample to estimate the standard error of the sample statistic. The standard error was then used to calculate a standardised test statistic, the z-score, which was used to get a p-value, so we could decide whether or not to reject the null hypothesis. A bootstrap distribution can be computationally intensive to calculate, so this time we'll instead calculate the test statistic without it.
## Standardised test statistic for proportions
An unknown population parameter that is a proportion, or population proportion for short, is denoted $p$. The sample proportion is denoted $\hat{p}$, and the hypothesised value for the population proportion is denoted $p_0$. As in Chapter 1, the standardised test statistic is a z-score. 
$$
z = \frac{\hat{p} - mean(\hat{p})}{SE(\hat{p})} = \frac{\hat{p} - p}{SE(\hat{p})}
$$
We calculate it by starting with the sample statistic, subtracting its mean, then dividing by its standard error. Recall from Sampling in Python that the mean of a sampling distribution of sample means, denoted by $\hat{p}$, is $p$, the population proportion. Under the null hypothesis, the unknown proportion $p$ is assumed to be the hypothesised population proportion $p_0$. The z-score is now:
$$
z =  \frac{\hat{p} - p_0}{SE(\hat{p})}
$$
## Simplifying the standard error calculations
For proportions, under $H_0$, the standard error of $\hat{p}$ equation can be simplified to:  
$$
SE_{\hat{p}} = \sqrt{\frac{p_0 * (1 - p_0)}{n}}
$$
We can substitute this into our equation for the z-score. This is easier to calculate because it only uses $\hat{p}$ and $n$, which we get from the sample, and $p_0$, which we chose.
$$
z = \frac{\hat{p} - p_0}{\sqrt{\frac{p_0 * (1 - p_0)}{n}}}
$$
## Why z instead of t?
We might wonder why we used a z-distribution here, but a t-distribution in Chapter 2. This is the test statistic equation for the two sample mean case. 
$$
t = \frac{(\bar{x}_{child} - \bar{x}_{adult})}{\sqrt{\frac{s^2_{child}}{n_{child}} + \frac{s^2_{adult}}{n_{adult}}}}
$$
The standard deviation of the sample, s, is calculated from the sample mean, $\bar{x}$. That means that $\bar{x}$ is used in the numerator to estimate the population mean, and in the denominator to estimate the population standard deviation. This dual usage increases the uncertainty in our estimate of the population parameter. Since t-distributions are effectively a normal distribution with fatter tails, we can use them to account for this extra uncertainty. In effect, the t-distribution provides extra caution against mistakenly rejecting the null hypothesis. For proportions, we only use $\hat{p}$ in the numerator, thus avoiding the problem with uncertainty, and a 
z-distribution is fine.
## Stack Overflow age categories
Returning to the Stack Overflow survey, let's hypothesise that half of the users in the population are under 30 and check for a difference. Let's set a significance level of 0.01. In the sample, just over half the users are under 30.
- $H_0$: Proportion of Stack Overflow users under thirty $= 0.5$
- $H_A$: Proportion of Stack Overflow users under thirty $\neq 0.5$
```Python
alpha = 0.01

stack_overflow['age_cat'].value_counts(normalize=True)
>>Under 30       0.535604
>>At least 30    0.464396
>>Name: age_cat, dtype: float64
```
## Variables for z
Let's get the numbers needed for the z-score. $\hat{p}$ is the proportion of sample rows where age_cat equals under thirty. $p_0 = 0.5$ according to the null hypothesis. $n$ is the number of rows in the dataset.
```Python
p_hat = (stack_overflow['age_cat'] == 'Under 30').mean()
>>0.5356037151702786

p_0 = 0.50

n = len(stack_overflow)
>>2261
```
## Calculating the z-score
Inserting the values we calculated into the z-score equation yields a z-score of around 3.4.
```Python
import numpy as np
numerator = p_hat - p_0
denominator = np.sqrt(p_0 * (1 - p_0) / n)
z_score = numerator / denominator
>>3.385911440783663
```
## Calculating the p-value
For left-tailed alternative hypotheses, we transform the z-score into a p-value using `norm.cdf()`. For right-tailed alternative hypotheses, we subtract the norm.cdf result from one. For two-tailed alternative hypotheses, we check whether the test statistic lies in either tail, so the p-value is the sum of these two values: one corresponding to the z-score and the other to its negative on the other side of the distribution. 
```Python
## Two-tailed
p_value = norm.cdf(-z_score) + 1 - norm.cdf(z_score)

p_value = 2 * (1 - norm.cdf(z_score))
>>0.0007094227368100725

p_value <= alpha
>>True
```
Since the normal distribution PDF is symmetric, this simplifies to twice the right-tailed p-value since the z-score is positive. Here, the p-value is less than the significance level of 0.01, so we reject the null hypothesis, concluding that the proportion of users under 30 is not equal to 0.5.
## Let's practice!
Let's try an example