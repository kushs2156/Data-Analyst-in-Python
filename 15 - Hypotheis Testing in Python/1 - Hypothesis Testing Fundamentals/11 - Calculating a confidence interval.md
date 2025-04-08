- Calculate a 95% confidence interval from `late_shipments_boot_distn` using the quantile method, labelling the lower and upper intervals `lower` and `upper`.
```Python
# Calculate 95% confidence interval using quantile method
lower = np.quantile(late_shipments_boot_distn, 0.025)
upper = np.quantile(late_shipments_boot_distn, 0.975)

# Print the confidence interval
print((lower, upper))
>>(0.047, 0.076)
```
Does the confidence interval match up with the conclusion to stick with the original assumption that 6% is a reasonable value for the unknown population parameter?
- Yes, since 0.06 is included in the 95% confidence interval and we failed to reject $H_0$ due to a large p-value, the results are similar.