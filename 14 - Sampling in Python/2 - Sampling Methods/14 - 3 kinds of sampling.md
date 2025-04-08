- Perform simple random sampling on `attrition_pop` to get one-quarter of the population, setting the seed to `2022`.
```Python
# Perform simple random sampling to get 0.25 of the population
attrition_srs = attrition_pop.sample(frac=0.25, random_state=2022)
```
- Perform stratified sampling on `attrition_pop` to sample one-quarter of each `RelationshipSatisfaction` group, setting the seed to `2022`.
```Python
# Perform stratified sampling to get 0.25 of each relationship group
attrition_strat = attrition_pop.groupby("RelationshipSatisfaction"). \
	sample(frac=0.25, random_state=2022)
```
- Create a list of unique values from `attrition_pop`'s `RelationshipSatisfaction` column.
- Randomly sample `satisfaction_unique` to get two values.
- Subset the population for rows where `RelationshipSatisfaction` is in `satisfaction_samp` and clear any unused categories from `RelationshipSatisfaction`; assign to `attrition_clust_prep`.
- Perform cluster sampling on the selected satisfaction groups, sampling one quarter of the _population_ and setting the seed to `2022`.
```Python
# Create a list of unique RelationshipSatisfaction values
satisfaction_unique = list(attrition_pop["RelationshipSatisfaction"] \
	.unique())

# Randomly sample 2 unique satisfaction values
satisfaction_samp = random.sample(satisfaction_unique, k=2)

# Filter for satisfaction_samp and clear unused categories from RelationshipSatisfaction
satis_condition = attrition_pop["RelationshipSatisfaction"] \
	.isin(satisfaction_samp)
attrition_clust_prep = attrition_pop[satis_condition]
attrition_clust_prep['RelationshipSatisfaction'] = 
	attrition_clust_prep['RelationshipSatisfaction'] \ 
		.cat.remove_unused_categories()

# Perform cluster sampling on the selected group, getting 0.25 of attrition_pop
attrition_clust = attrition_clust_prep \ 
	.groupby('RelationshipSatisfaction')
		.sample(n=len(attrition_pop) // 4, random_state=2022)
```