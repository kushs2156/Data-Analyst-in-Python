- What type of test does the alternative hypothesis indicate that we need?
Left-tailed

- Calculate the degrees of freedom for the test.
- Compute the p-value using the test statistic, `t_stat`.
```Python
# Calculate the degrees of freedom
degrees_of_freedom = n_no + n_yes - 2

# Calculate the p-value from the test stat
p_value = t.cdf(t_stat, df=degrees_of_freedom)

# Print the p_value
print(p_value)
>>0.008432382146249523
```
What decision should you make based on the results of the hypothesis test?
- Reject the null hypothesis