So what do we do if the assumptions for the hypothesis tests we've seen so far aren't met?
## Parametric tests
The tests that we've seen so far are known as parametric tests. Tests like the z-test, 
t-test, and ANOVA are all based on the assumption that the population is normally distributed. Parametric tests also require sample sizes that are "big enough" that the Central Limit Theorem applies.
## Smaller Republican votes data
Let's study a case where the sample size requirement isn't met with a subset of the US Presidential voting results for Republican candidates that we examined in a previous chapter. Here, repub_votes_small contains only five counties randomly sampled from the larger dataset of 2008 and 2012 county-level returns.
## Results with `pingouin.ttest()`
Let's try performing a paired t-test on this small sample. Recall that we require 30 pairs to feel confident in using a t-test, and this sample only contains 5. We set a significance level of 1% and use the ttest method from pingouin to perform the left-tailed paired t-test. 
```Python
alpha = 0.01
import pingouin
pingouin.ttest(x=repub_votes_potus_08_12_small['repub_percent_08'],
			   y=repub_votes_potus_08_12_small['repub_percent_12'],
			   paired=True,
			   alternative="less")
```
The small p-value indicates we should reject the null hypothesis, leading us to suspect that the 2008 election had a smaller percentage of Republican votes than the 2012 election.
## Non-parametric tests
In situations where we aren't sure about these assumptions, or we are certain that the assumptions aren't met, we can use non-parametric tests. They do not make the normal distribution assumptions or the sample size conditions that we saw in the previous video. There are many different ways to perform tests without these parametric assumptions. In this chapter, we'll focus on those relating to ranks. Consider the list, x. 
`x = [1, 15, 3, 10, 6]`
The first value of x, 1, is the smallest value and the second value, 15, is the fifth smallest. These orderings from smallest to largest are known as the ranks of the elements of x. We can access them with the `rankdata()` method from scipy.stats.
```Python
from scipy.stats import rankdata
rankdata(x)
>>array([1., 5., 2., 4., 3.])
```

Let's now use a non-parametric test to see what kind of results it gives. Remember that non-parametric tests work better than the parametric alternative in situations where the sample size is small or the data cannot be assumed to be normally distributed. We will use the Wilcoxon-signed rank test, which was developed by Frank Wilcoxon in 1945 and was one of the first non-parametric procedures developed. We'll go over the inner workings of the test before implementing it using another pingouin method.
## Wilcoxon-signed rank test (Step 1)
The Wilcoxon-signed rank test requires us to calculate the absolute differences in the pairs of data and then rank them. First, we take the differences in the paired values.
```Python
repub_votes_small['diff'] = repub_votes_small['repub_percent_08'] -
							repub_votes_small['repub_percent_12']
print(repub_votes_small)
```
## Wilcoxin-signed rank test (Step 2)
Next, we take the absolute value of the differences, using the `.abs()` method, and place them in the abs_diff column.
```Python
repub_votes_small['abs_diff'] = repub_votes_small['diff'].abs()
```
## Wilcoxin-signed rank test (Step 3)
Then, we rank these absolute differences using the rankdata method from scipy.stats.
```Python
from scipy.stats import rankdata
repub_votes_small['rank_abs_diff'] = 
	rankdata(repub_votes_small['abs_diff'])
print(repub_votes_small)
```
## Wilcoxin-signed rank test (Step 4)
The last part of our calculation involves calculating a test statistic called `W`. `W` uses the signs of the diff column to split the ranks into two groups: one for rows with negative differences and one for positive differences. `T_minus` is defined as the sum of the ranks with negative differences, and `T_plus` is the sum of the ranks with positive differences. For this example, all the differences are negative, so the `T_minus` value is the sum of the five ranks, and T-plus is zero. 
```Python
T_minus = 1 + 4 + 5 + 2 + 3
T_plus = 0

W = np.min([T_minus, T_plus])
>>0
```
The test statistic W is the smaller of `T_minus` and `T_plus`, which in this case, is zero. We can calculate W, and its corresponding p-value, using a pingouin method instead of manual calculation.
## Implementation with `pingouin.wilcoxon()`
The `.wilcoxon()` method from pingouin takes very similar arguments to the dot-ttest method, except it doesn't have a paired argument. The function returns a W value of zero - the same as our manual calculation! 
```Python
alpha = 0.01
pingouin.wilcoxon(x=repub_votes_potus_08_12_small['repub_percent_08'],
				  y=repub_votes_potus_08_12_small['repub_percent_12'],
				  alternative="less")
```
This corresponds to a p-value of around 3%, which is over 10 times larger than the p-value from the t-test, so we should feel more confident with this result given the small sample size. The Wilcoxon test indicates that we do not have evidence that the 2008 Republican percentages are smaller than the 2012 percentages using this small sample of five rows.
## Let's practice!
Get your Wilcoxon!