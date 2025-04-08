In order to determine whether to choose the null hypothesis or the alternative hypothesis, you need to calculate a p-value from the z-score.

You'll now return to the late shipments dataset and the proportion of late shipments.

The null hypothesis, $H_0$, is that the proportion of late shipments is six percent.

The alternative hypothesis, $H_A$, is that the proportion of late shipments is **greater than** six percent.

The observed sample statistic, `late_prop_samp`, the hypothesized value, `late_prop_hyp` (6%), and the bootstrap standard error, `std_error` are available. `norm` from `scipy.stats` has also been loaded without an alias.

What type of test should be used for this alternative hypothesis?
- Right-tailed

- Calculate the z-score of `late_prop_samp`.
- Calculate the p-value for the z-score, using a right-tailed test.
```Python
# Calculate the z-score of late_prop_samp
z_score = (late_prop_samp - late_prop_hyp) / std_error

# Calculate the p-value
p_value = 1 - norm.cdf(z_score, loc=0, scale=1)

# Print the p-value
print(p_value)
>>0.4468840678346485
```