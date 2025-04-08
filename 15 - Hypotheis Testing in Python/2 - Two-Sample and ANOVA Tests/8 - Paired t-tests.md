Previously, we used the t-distribution to compute a p-value from a standardised test statistic related to the difference in means across two groups.

Here's a dataset of US presidential elections. Each row represents a presidential election at the county level. The variables in the dataset are the US state, the county within that state, and the percentage of votes for the Republican candidate in 2008, and in 2012.

One question is whether the percentage of votes for the Republican candidate was lower in 2008 compared to 2012. To test this, we form hypotheses. As before, the null hypothesis is that our hunch is wrong, and that the population parameters are the same in each year group. The alternative hypothesis is that the parameter in 2008 was lower than in 2012. 
$$
\begin{align}
H_{0} &: \mu_{2008} - \mu_{2012} = 0 \\
H_{A} &: \mu_{2008} - \mu_{2012} < 0
\end{align}
$$
Let's set a significance level of 0.05. One feature of this dataset is that the 2008 votes and the 2012 votes are paired, which means they aren't independent, since they both refer to the same county. This means voting patterns may occur due to county-level demographics and local politics, and we want to capture this pairing in our model.
## From two samples to one
For paired analyses, rather than considering the two variables separately, we can consider a single variable of the difference. This is stored in a DataFrame called sample_data with a column named diff. 
```Python
sample_data = repub_votes_potus_08_12
sample_data['diff'] = sample_data['repub_percent_08'] - 
					  sample_data['repub_percent_12']
```
In this histogram of the difference, most values are between -10 and 10, with at least one outlier.
```Python
import matplotlib.pyplot as plt
sample_data['diff'].hist(bins=20)
```
The sample mean, $\bar{x}$, is calculated from this difference. It is around -2.88.
```Python
xbar_diff = sample_data['diff'].mean()
```
## Revised hypotheses
We can restate the hypotheses in terms of the single population mean, $\mu_{diff}$, being equal to or less than zero. 
$$
\begin{align}
H_{0} &: \mu_{diff} = 0 \\
H_{A} &: \mu_{diff} < 0
\end{align}
$$
The test statistic, t, has a slightly simpler equation compared to the two sample case. We have one statistic, so the number of degrees of freedom is the number of pairs minus one.
$$
t = \frac{\bar{x}_{diff} - \mu_{diff}}{\sqrt{\frac{s^2_{diff}}{n_{diff}}}}
$$
$$
df = n_{diff} - 1
$$
## Calculating the p-value
To calculate the test statistic, we need the number of rows in the dataset, 100, and the standard deviation of the differences. We already calculated $\bar{x}_{diff}$, the mean of the differences, as -2.88. Assuming the null hypothesis is true means $\mu_{diff} = 0$. We now have everything we need to plug into the equation to calculate t. 
```Python
n_diff = len(sample_data)
>>100

s_diff = sample_data['diff'].std()

t_stat = (xbar_diff-0) / np.sqrt(s_diff ** 2 / n_diff)
>>-5.6010432121928489
```
It's -5.6. The degrees of freedom are one less than $n_{diff}$ at 99. 
```Python
degrees_of_freedom = n_diff - 1
>>99
```
Finally, we transform t with the t-distribution CDF. The p-value is really small at around $9.6 \times 10^{-8}$. That means we reject the null hypothesis in favour of the alternative hypothesis that the Republican candidates got a smaller percentage of the vote in 2008 compared to 2012.
```Python
from scipy.stats import t
p_value = t.cdf(t_stat, df=n_diff-1)
>>9.572537285272411e-08
```
## Testing differences between two means using `ttest()`
That was a lot of calculating. Fortunately, there's an easier way. The `pingouin` package provides a variety of different methods for hypothesis testing and returns the results as a pandas DataFrame. Its output can be a little friendlier to work with than similar methods from scipy.stats. One method from pingouin is `.ttest()` and it works with array-like objects, so the first argument is the Series of differences. For a converted one sample test like this, y specifies the hypothesised difference value from the null hypothesis, which is zero. The type of alternative hypothesis can be specified as "two-sided", "less", or "greater", corresponding to two-tailed, left-tailed, and right-tailed tests, respectively. 
```Python
import pingouin
pingouin.ttest(x=sample_date['diff'],
			   y=0,
			   alternative="less")
```
Here's the output. We can recognise the value of the test statistic, the degrees of freedom, the alternative direction, and the p-value. The additional output refers to more advanced statistical concepts that are outside the scope of this course.
## `ttest()` with `paired=True`
There's a variation of ttest for paired data that requires even less work. Rather than calculating the difference between the two paired variables, we can just pass them both directly to ttest as x and y, and set paired to True. Notice that the results in the first four columns are the same as before.
```Python
pingouin.ttest(x=sample_data['repub_percent_08'],
			   y=sample_data['repub_percent_12'],
			   paired=True,
			   alternative="less")
```
## Unpaired `ttest()`
If we don't set paired to True and instead perform an unpaired t-test, then the numbers change. The test statistic is closer to zero, there are more degrees of freedom, and the p-value is much larger. Performing an unpaired t-test when our data is paired increases the chances of false negative errors.
```Python
pingouin.ttest(x=sample_data['repub_percent_08'],
			   y=sample_data['repub_percent_12'],
			   paired=False, # The default
			   alternative="less")
```
## Let's practice!
Time to perform some pairing.