- Use equal counts stratified sampling on `attrition_pop` to get 30 employees from each `Education` group, setting the seed to `2022`.
- Get the proportion of employees by `Education` level from `attrition_eq`.
```Python
# Get 30 employees from each Education group
attrition_eq = attrition_pop.groupby("Education").sample(n=30, 
									random_state=2022)

# Print the sample
print(attrition_eq)

# Get the proportions from attrition_eq
education_counts_eq = attrition_eq["Education"].value_counts( \ 
								normalize=True)

# Print the results
print(education_counts_eq)
```
