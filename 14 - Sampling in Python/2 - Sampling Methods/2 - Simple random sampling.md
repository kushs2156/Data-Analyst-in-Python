- Sample 70 rows from `attrition_pop` using simple random sampling, setting the random seed to `18900217`.
- Print the sample dataset, `attrition_samp`. _What do you notice about the indices?_
```Python
# Sample 70 rows using simple random sampling and set the seed
attrition_samp = attrition_pop.sample(n=70, random_state=18900217)

# Print the sample
print(attrition_samp)
```
