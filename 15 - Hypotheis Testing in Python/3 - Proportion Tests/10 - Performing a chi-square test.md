- Calculate the proportion of `freight_cost_group` in `late_shipments` grouped by `vendor_inco_term`.
- Unstack the `.value_counts()` result to be in wide format instead of long.
- Create a proportional stacked bar plot with bars filled based on `freight_cost_group` across the levels of `vendor_inco_term`.
- Perform a chi-square test of independence on `freight_cost_group` and `vendor_inco_term` in the `late_shipments` dataset.
```Python
# Proportion of freight_cost_group grouped by vendor_inco_term
props = late_shipments.groupby('vendor_inco_term')\
			['freight_cost_group'].value_counts(normalize=True)

# Print props
print(props)

# Convert props to wide format
wide_props = props.unstack()

# Print wide_props
print(wide_props)

# Proportional stacked bar plot of freight_cost_group vs. 
# vendor_inco_term
wide_props.plot(kind="bar", stacked=True)
plt.show()

# Determine if freight_cost_group and vendor_inco_term are independent
expected, observed, stats = pingouin.chi2_independence(\
							data=late_shipments, 
							x="vendor_inco_term", 
							y="freight_cost_group")

# Print results
print(stats[stats['test'] == 'pearson'])
>>      test  lambda    chi2  dof       pval  cramer  power 
>>0  pearson     1.0  28.941  3.0  2.304e-06    0.17  0.998
```
![[download 133.svg]]
- What should you conclude from the hypothesis test?
Reject the null hypothesis and conclude that `vendor_inco_term` and `freight_cost_group` are associated.