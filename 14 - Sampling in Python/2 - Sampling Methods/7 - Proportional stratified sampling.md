- Get the proportion of employees by `Education` level from `attrition_pop`.
- Use proportional stratified sampling on `attrition_pop` to sample 40% of each `Education` group, setting the seed to `2022`.
- Get the proportion of employees by `Education` level from `attrition_strat`.
```Python
# Proportion of employees by Education level
education_counts_pop = attrition_pop["Education"].value_counts( \ 
										normalize=True)

# Print education_counts_pop
print(education_counts_pop)

# Proportional stratified sampling for 40% of each Education group
attrition_strat = attrition_pop.groupby("Education").sample( \ 
						frac=0.4, random_state=2022)

# Print the sample
print(attrition_strat)

# Calculate the Education level proportions from attrition_strat
education_counts_strat = attrition_strat['Education'].value_counts( \ 
									normalize=True)

# Print education_counts_strat
print(education_counts_strat)
```
