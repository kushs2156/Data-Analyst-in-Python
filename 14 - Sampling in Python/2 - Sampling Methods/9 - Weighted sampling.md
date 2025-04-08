- Plot `YearsAtCompany` from `attrition_pop` as a histogram with bins of width `1` from `0` to `40`.
- Sample 400 employees from `attrition_pop` weighted by `YearsAtCompany`.
- Plot `YearsAtCompany` from `attrition_weight` as a histogram with bins of width `1` from `0` to `40`.
```Python
# Plot YearsAtCompany from attrition_pop as a histogram
attrition_pop["YearsAtCompany"].hist(bins=np.arange(0, 41, 1))
plt.show()

# Sample 400 employees weighted by YearsAtCompany
attrition_weight = attrition_pop.sample(n=400, 
								weights="YearsAtCompany")

# Print the sample
print(attrition_weight)

# Plot YearsAtCompany from attrition_weight as a histogram
attrition_weight['YearsAtCompany'].hist(bins=np.arange(0, 41, 1))
plt.show()
```
![[download 125.svg]]
![[download 126.svg]]
Which is higher? The mean `YearsAtCompany` from `attrition_pop` or the mean `YearsAtCompany` from `attrition_weight`?
- Sample mean