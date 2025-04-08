- Calculate the pooled sample proportion, p^, from `p_hats` and `ns`.
$$
\hat{p} = \frac{n_{expensive} \times \hat{p}_{expensive} + n_{reasonable} \times \hat{p}_{reasonable}}{n_{expensive} + n_{reasonable}}
$$
$$
SE(\hat{p}_{\geq 30}- \hat{p}_{<30}) = \sqrt{\frac{\hat{p} \times (1 - \hat{p})}{n_{\geq 30}} + \frac{\hat{p} \times (1 - \hat{p})}{n_{< 30}}}
$$
- Calculate `p_hat` multiplied by `(1 - p_hat)`.
- Divide `p_hat_times_not_p_hat` by the number of `"reasonable"` rows and by the number of `"expensive"` rows, and sum those two values.
- Calculate `std_error` by taking the square root of `p_hat_times_not_p_hat_over_ns`.
- Calculate the z-score _using the following equation.
$$
z = \frac{(\hat{p}_{expensive} - \hat{p}_{reasonable})}{SE(\hat{p}_{expensive}- \hat{p}_{reasonable})}
$$
- Calculate the p-value from the z-score.
```Python
# Calculate the pooled estimate of the population proportion
p_hat = (ns['expensive'] * p_hats['expensive', 'Yes'] 
		+ ns['reasonable'] * p_hats['reasonable', 'Yes']) / 
		(ns['expensive'] + ns['reasonable'])

# Print the result
print(p_hat)
>>0.061

# Calculate p_hat one minus p_hat
p_hat_times_not_p_hat = p_hat * (1 - p_hat)

# Divide this by each of the sample sizes and then sum
p_hat_times_not_p_hat_over_ns = 
				p_hat_times_not_p_hat/ns['expensive'] + 
				p_hat_times_not_p_hat/ns['reasonable']

# Calculate the standard error
std_error = np.sqrt(p_hat_times_not_p_hat_over_ns)

# Print the result
print(std_error)
>>late
>>Yes   0.015

# Calculate the z-score
z_score = (p_hats['expensive', 'Yes'] - 
		   p_hats['reasonable', 'Yes']) / std_error

# Print z_score
print(z_score)
>>late
>>Yes   3.119

# Calculate the p-value from the z-score
p_value = 1 - norm.cdf(z_score)

# Print p_value
print(p_value)
>>[0.00090721]
```
