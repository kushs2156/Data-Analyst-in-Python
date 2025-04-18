- Create a list of unique `JobRole` values from `attrition_pop`, and assign to `job_roles_pop`.
- Randomly sample four `JobRole` values from `job_roles_pop`.
- Subset `attrition_pop` for the sampled job roles by filtering for rows where `JobRole` is in `job_roles_samp`.
- Remove any unused categories from `JobRole`.
- For each job role in the filtered dataset, take a random sample of ten rows, setting the seed to `2022`.
```Python
# Create a list of unique JobRole values
job_roles_pop = list(attrition_pop["JobRole"].unique())

# Randomly sample four JobRole values
job_roles_samp = random.sample(job_roles_pop, k=4)

# Print the result
print(job_roles_samp)

# Filter for rows where JobRole is in job_roles_samp
jobrole_condition = attrition_pop['JobRole'].isin(job_roles_samp)
attrition_filtered = attrition_pop[jobrole_condition]

# Print the result
print(attrition_filtered)

# Remove categories with no rows
attrition_filtered['JobRole'] = attrition_filtered['JobRole'] \
					.cat.remove_unused_categories()

# Randomly sample 10 employees from each sampled job role
attrition_clust = attrition_filtered.groupby('JobRole').sample(n=10, 
								random_state=2022)

# Print the sample
print(attrition_clust)
```