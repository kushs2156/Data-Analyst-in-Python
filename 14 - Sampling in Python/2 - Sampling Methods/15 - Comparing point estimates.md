- Group `attrition_pop` by `RelationshipSatisfaction` levels and calculate the mean of `Attrition` for each level.
```Python
# Mean Attrition by RelationshipSatisfaction group
mean_attrition_pop = attrition_pop \ 
	.groupby('RelationshipSatisfaction')["Attrition"].mean()

# Print the result
print(mean_attrition_pop)
```
- Calculate the proportion of employee attrition for each relationship satisfaction group, this time on the simple random sample, `attrition_srs`.
```Python
# Calculate the same thing for the simple random sample 
mean_attrition_srs = attrition_srs \ 
	.groupby("RelationshipSatisfaction")["Attrition"].mean()

# Print the result
print(mean_attrition_srs)
```
- Calculate the proportion of employee attrition for each relationship satisfaction group, this time on the stratified sample, `attrition_strat`.
```Python
# Calculate the same thing for the stratified sample 
mean_attrition_strat = attrition_strat \ 
	.groupby("RelationshipSatisfaction")["Attrition"].mean()

# Print the result
print(mean_attrition_strat)
```
- Calculate the proportion of employee attrition for each relationship satisfaction group, this time on the cluster sample, `attrition_clust`.
```Python
# Calculate the same thing for the cluster sample 
mean_attrition_clust = attrition_clust \ 
	.groupby("RelationshipSatisfaction")["Attrition"].mean()

# Print the result
print(mean_attrition_clust)
```

