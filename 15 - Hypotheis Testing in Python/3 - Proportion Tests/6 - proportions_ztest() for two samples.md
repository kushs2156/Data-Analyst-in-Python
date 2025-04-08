- Get the counts of the `late` column grouped by `freight_cost_group`.
- Extract the number of `"Yes"`'s for the two `freight_cost_group` into a `numpy` array, specifying the `'expensive'` count and then `'reasonable'`.
- Determine the overall number of rows in each `freight_cost_group` as a `numpy` array, specifying the `'expensive'` count and then `'reasonable'`.
- Run a z-test using `proportions_ztest()`, specifying `alternative` as `'larger'`.
```Python
# Count the late column values for each freight_cost_group
late_by_freight_cost_group = 
	late_shipments.groupby('freight_cost_group')['late'].value_counts()

# Print the counts
print(late_by_freight_cost_group)

# Create an array of the "Yes" counts for each freight_cost_group
success_counts = np.array([45, 16])

# Create an array of the total number of rows in each 
# freight_cost_group
n = np.array([545, 455])

# Run a z-test on the two proportions
stat, p_value = proportions_ztest(count=success_counts, 
								  nobs=n, 
								  alternative="larger")

# Print the results
print(stat, p_value)
>>3.1190401865206128 0.0009072060637051224
```