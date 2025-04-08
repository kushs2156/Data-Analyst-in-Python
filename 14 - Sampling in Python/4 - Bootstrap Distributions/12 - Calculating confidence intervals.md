- Generate a 95% confidence interval using the quantile method on the bootstrap distribution, setting the `0.025` quantile as `lower_quant` and the `0.975` quantile as `upper_quant`.
```Python
# Generate a 95% confidence interval using the quantile method
lower_quant = np.quantile(bootstrap_distribution, 0.025)
upper_quant = np.quantile(bootstrap_distribution, 0.975)

# Print quantile method confidence interval
print((lower_quant, upper_quant))
>>(54.56816, 55.1674)
```
Generate a 95% confidence interval using the standard error method from the bootstrap distribution.
- Calculate `point_estimate` as the mean of `bootstrap_distribution`, and `standard_error` as the standard deviation of `bootstrap_distribution`.
- Calculate `lower_se` as the `0.025` quantile of an inv. CDF from a normal distribution with mean `point_estimate` and standard deviation `standard_error`.
- Calculate `upper_se` as the `0.975` quantile of that same inv. CDF.
```Python
# Find the mean and std dev of the bootstrap distribution
point_estimate = np.mean(bootstrap_distribution)
standard_error = np.std(bootstrap_distribution, ddof=1)

# Find the lower limit of the confidence interval
lower_se = norm.ppf(0.025, loc=point_estimate, scale=standard_error)

# Find the upper limit of the confidence interval
upper_se = norm.ppf(0.975, loc=point_estimate, scale=standard_error)

# Print standard error method confidence interval
print((lower_se, upper_se))
>>(54.56464443118767, 55.16750236881231)
```