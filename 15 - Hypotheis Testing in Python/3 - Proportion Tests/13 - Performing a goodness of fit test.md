- Using the `incoterm_counts` and `hypothesized` datasets, perform a chi-square goodness of fit test on the incoterm counts, `n`.
```Python
# Perform a goodness of fit test on the incoterm counts n
gof_test = chisquare(f_obs=incoterm_counts['n'], 
					 f_exp=hypothesized['n'])

# Print gof_test results
print(gof_test)
Power_divergenceResult(statistic=2.3633633633633613, 
					   pvalue=0.5004909543758689)
```
- What should you conclude from the hypothesis test?
Fail to reject the null hypothesis and conclude that `n` follows the distribution specified by `hypothesized`.