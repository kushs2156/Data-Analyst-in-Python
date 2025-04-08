- Set the sample size to `70`.
- Calculate the population size from `attrition_pop`.
- Calculate the interval between the rows to be sampled.
- Systematically sample `attrition_pop` to get the rows of the population at each `interval`, starting at 0; assign the rows to `attrition_sys_samp`.
```Python
# Set the sample size to 70
sample_size = 70

# Calculate the population size from attrition_pop
pop_size = len(attrition_pop)

# Calculate the interval
interval = pop_size // sample_size

# Systematically sample 70 rows
attrition_sys_samp = attrition_pop.iloc[::interval]

# Print the sample
print(attrition_sys_samp)
```
