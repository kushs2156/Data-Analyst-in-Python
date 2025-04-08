- Find the 25th percentile of `"Salary_USD"`.
- Store the median of `"Salary_USD"` as `salaries_median`.
- Get the 75th percentile of salaries.
```Python
# Find the 25th percentile
twenty_fifth = salaries["Salary_USD"].quantile(0.25)

# Save the median
salaries_median = salaries["Salary_USD"].median()

# Gather the 75th percentile
seventy_fifth = salaries["Salary_USD"].quantile(0.75)
print(twenty_fifth, salaries_median, seventy_fifth)
```
