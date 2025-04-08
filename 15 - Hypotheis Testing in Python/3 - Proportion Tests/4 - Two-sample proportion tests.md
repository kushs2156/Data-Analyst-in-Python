Great work so far! In the previous lesson, we tested a single proportion against a specific value. As with means, we can also test for differences between proportions in two populations. The Stack Overflow survey contains a hobbyist variable. The value "Yes" means the user described themselves as a hobbyist and "No" means they described themselves as a professional. We can hypothesise that the proportion of hobbyist users is the same for the under thirty age category as the thirty or over category, which is a two-tailed test. More formally, the null hypothesis is that the difference between the population parameters for each group is zero. Let's set a significance level of 0.05.
- $H_0$: Proportion of hobbyist users is the same for those under thirty as those at least thirty
  $H_0: p_{\geq 30}- p_{<30} = 0$
- $H_A$: Proportion of hobbyist users is different for those under thirty to those at least thirty
  $H_A: p_{\geq 30}- p_{<30} \neq 0$
## Calculating the z-score
Here is the z-score equation for a proportion test. Let's break it down. 
$$
z = \frac{(\hat{p}_{\geq 30} - \hat{p}_{<30}) - 0}{SE(\hat{p}_{\geq 30}- \hat{p}_{<30})}
$$
The sample statistic is the difference in the proportions for each category. That's the two $\hat{p}$ values in the numerator. We subtract the hypothesised value of the population parameter, and assuming the null hypothesis is true, it's zero. The denominator is the standard error of the sample statistic. We can again avoid having to generate a bootstrap distribution to calculate the standard error by using a standard error equation, which is a slightly more complicated version of the one sample case. 
$$
SE(\hat{p}_{\geq 30}- \hat{p}_{<30}) = \sqrt{\frac{\hat{p} \times (1 - \hat{p})}{n_{\geq 30}} + \frac{\hat{p} \times (1 - \hat{p})}{n_{< 30}}}
$$
Note that $\hat{p}$ is a ==weighted mean of the sample proportions for each category==, also is known as a pooled estimate of the population proportion. $\hat{p}$ can be calculated using the following equation. 
$$
\hat{p} = \frac{n_{\geq 30} \times \hat{p}_{\geq 30} + n_{< 30} \times \hat{p}_{< 30}}{n_{\geq 30} + n_{< 30}}
$$
This looks horrendous, but Python is great at handling arithmetic. We now only need four numbers from the sample dataset to perform these calculations and calculate the z-score: the proportion of hobbyists in each age group, and the number of observations in each age group.
## Getting the numbers for the z-score
To calculate these four numbers, we group by the age category, and calculate the sample proportions using `.value_counts()`, and the row counts using `.count()`. As we're looking at the proportion of hobbyists, we'll only be focusing on rows where hobbyist is Yes.
```Python
p_hats = stack_overflow.groupby("age_cat")['hobbyist']\
	.value_counts(normalize=True)

n = stack_overflow.groupby('age_cat')['hobbyist'].count()
```
To isolate the hobbyist proportions from p_hats, we can use pandas' multiIndex subsetting, passing a tuple of the outer column and inner column values. 
```Python
p_hat_at_least_30 = p_hats[("At least 30", "Yes")]
p_hat_under_30 = p_hats[("Under 30", "Yes")]
print(p_hat_at_least_30, p_hat_under_30)
>>0.773333 0.843105
```
This returns a sample proportion of 0.77 for the at least thirty group, and 0.84 for the under thirty's. The number of observations in each age category can be extracted with simpler pandas subsetting. There are 1050 rows in the at least thirty group and 1211 for the under 30 group.
```Python
n_at_least_30 = n["At least 30"]
n_under_30 = n["Under 30"]
print(n_at_least_30, n_under_30)
>>1050 1211
```
After that, we can do the arithmetic using our equations for $\hat{p}$, the standard error, and the z-score to get the test statistic. This returns a z-score of -4.22. Luckily, we can avoid much of this arithmetic.
```Python
p_hat = (n_at_least_30 * p_hat_at_least_30 + 
		 n_under_30 * p_hat_under_30) /
		 (n_at_least_30 + n_under_30)

std_error = np.sqrt(p_hat * (1-p_hat) / n_at_least_30 +
					p_hat * (1-p_hat) / n_under_30)

z_score = (p_hat_at_least_30 - p_hat_under_30) / std_error
print(z_score)
>>-4.223718652693034
```
## Proportions tests using `proportions_ztest()`
The `proportions_ztest()` function from `statsmodels` can calculate the z-score more directly. This function requires two objects as NumPy arrays: the number of hobbyists in each age group, and the total number of rows in each age group. 
```Python
n_hobbyists = np.array([812, 1021])
n_rows = np.array([812 + 238, 1021 + 190])
```
We can get these numbers by grouping by age_cat, and calling .value_counts on the hobbyist column, as shown above. The numbers can then either be read-off or subsetted to create the arrays. Next, we import `proportions_ztest` from `statsmodels.stats.proportions`, and pass the arrays to the count and nobs arguments. Because we're testing for a difference, we specify that this is a two-sided test using the alternative argument. 
```Python
from statsmodels.stats.proportion import proportions_ztest
z_score, p_value = proportions_ztest(count=n_hobbyists, nobs=n_rows,
									 alternative="two-sided")

(-4.223691463320559, 2.403330142685068e-05)
```
proportions_ztest returns a z-score and a p-value. The p-value is smaller than the 5% significance level we specified, so we can conclude that there is a difference in the proportion of hobbyists between the two age groups.
## Let's practice!
Time to perform your own proportion tests.
