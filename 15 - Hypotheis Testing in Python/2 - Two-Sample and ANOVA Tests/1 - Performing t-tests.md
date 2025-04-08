In the previous chapter, we calculated the z-score, which was a test statistic for a single variable.
## Two-sample problems
Here, we'll look at a related problem of comparing sample statistics across groups in a variable. In the Stack Overflow dataset, converted_comp is a numerical variable of annual compensation. age_first_code_cut is a categorical variable with two levels: child and adult, which describe when the user started programming. We can ask questions about differences in compensation across the two age groups, such as, are users who first programmed as a child better compensated than those that started as adults?
## Hypothesis
The null hypothesis is that the population mean for the two groups is the same, and the alternative hypothesis is that the population mean for users who started coding as children is greater than for users who started coding as adults. We can write these hypotheses using equations. $\mu$ represents an unknown population mean, and we use subscripts to denote which group the population mean belongs to. An alternate way of writing the equations is to compare the differences in population means to zero. Zero here corresponds to our hypothesised value for the difference in means.
$$
\begin{align}
H_{0} &:\mu_{child} = \mu_{adult} \\
H_{0} &:\mu_{child} - \mu_{adult} = 0
\end{align}
$$
$$
\begin{align}
H_{A} &: \mu_{child} > \mu_{adult} \\
H_{A} &: \mu_{child} - \mu_{adult} > 0
\end{align}
$$
## Calculating groupwise summary statistics
To calculate summary statistics for each group, we start with the sample, group by the categorical variable, and then compute on the numeric variable. A pandas way of doing this is shown, calculating the mean of the converted_comp column after grouping by age_first_code_cut. 
```Python
stack_overflow.groupby('age_first_code_cut')['converted_comp'].mean()
>>age_first_code_cut
>>adult    111313.311047
>>child    132419.570621
>>Name: converted_comp, dtype: float64
```
Here, the child programmers have a mean compensation of $132,000 compared to around $111,000 for adult programmers. Is that increase statistically significant or could it be explained by sampling variability?
## Test statistics
Although we don't know the population mean, we estimate it using the sample mean. $\bar{x}$ is used to denote a sample mean. Then we use subscripts to denote which group a sample mean corresponds to ($\bar{x}_{child} , \bar{x}_{adult}$). The difference between these two sample means is the test statistic for the hypothesis test. The z-scores we saw in Chapter 1 are a type of standardised test statistic.
## Standardising the test statistic
z-scores are calculated by taking the sample statistic, subtracting the mean of this statistic as the population parameter of interest, then dividing by the standard error. In the two sample case, the test statistic, denoted $t$, uses a similar equation. We take the difference between the sample statistics for the two groups, subtract the population difference between the two groups, then divide by the standard error.
$$
\begin{align}
t &= \frac{difference \, in \, sample \, stats - difference \, in \, population \, parameters}{standard error} \\
t &= \frac{(\bar{x}_{child}-\bar{x}_{adult})-(\mu_{child}-\mu_{adult})}{SE(\bar{x}_{child}-\bar{x}_{adult})}
\end{align}
$$
## Standard error
To calculate the standard error, needed for the denominator of the test statistic equation, bootstrapping tends to be a good option. However, there is an easier way to approximate it. We calculate the standard deviation of the numeric variable for each group in the sample, and the number of observations in each group. Then enter those values into the equation and compute the result.
$$
SE(\bar{x}_{child}-\bar{x}_{adult}) \approx \sqrt{\frac{s^2_{child}}{n_{child}} + \frac{s^2_{adult}}{n_{adult}}}
$$
- $s$ is the standard deviation of the variable
- $n$ is the sample size (number of observations/rows in sample)
## Assuming the null hypothesis is true
Here's the test statistic equation again. If we assume that the null hypothesis is true, there's a simplification we can make. The null hypothesis assumes that the population means are equal, and their difference is zero, so the population term in the numerator disappears. 
$$
H_{0}: \mu_{child} - \mu_{adult} = 0 \rightarrow t = \frac{(\bar{x}_{child} - \bar{x}_{adult})}{SE(\bar{x}_{child}-\bar{x}_{adult})}
$$
Inserting the approximation for the standard error, we now have a way of calculating the test statistic using only calculations on the sample dataset.
$$
t = \frac{(\bar{x}_{child} - \bar{x}_{adult})}{\sqrt{\frac{s^2_{child}}{n_{child}} + \frac{s^2_{adult}}{n_{adult}}}}
$$
We need the mean, standard deviation, and number of observations for each group to fill in the formula for t. We again use `.groupby()` and method combinations with mean, std, and count.
```Python
xbar = stack_overflow.groupby('age_first_code_cut')['coverted_comp']\
	.mean()
>>adult     111313.311047
>>child     132419.570621
```
```Python
s = stack_overflow.groupby('age_first_code_cut')['coverted_comp']\
	.std()
>>adult     271546.521729
>>child     255585.240115
```
```Python
n = stack_overflow.groupby('age_first_code_cut')['coverted_comp']\
	.count()
>>adult     1376
>>child      885
```
## Calculating the test statistic
Assigning the values to six different variables, the numerator is a subtraction of the sample means, and the denominator is like a weighted hypotenuse. The t-statistic is around 1.87. Just as with z-scores, we can't draw any conclusions yet; for that, we'll need to wait for the next video.
```Python
import numpy as np
numerator = xbar_child = xbar_adult
denominator = np.sqrt(s_child ** 2 / n_child + s_adult ** 2 / n_adult)
t_stat = numerator / denominator
>>1.8699313316221844
```
## Let's practice!
In the mean time, let's calculate some test statistics.