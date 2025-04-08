- Conduct a paired t-test on the percentage columns using an appropriate alternative hypothesis.
```Python
# Conduct a paired t-test on dem_percent_12 and dem_percent_16
paired_test_results = pingouin.ttest(
					  x=sample_dem_data['dem_percent_12'], 
					  y=sample_dem_data['dem_percent_16'], 
					  paired=True, 
					  alternative='two-sided') 

# Print paired t-test results
print(paired_test_results)
>>             T  dof  alternative       p-val         CI95% 
>>T-test  30.298  499    two-sided  3.601e-115  [6.39, 7.27]
```
- Conduct a Wilcoxon-signed rank test on the same columns.
```Python
# Conduct a Wilcoxon test on dem_percent_12 and dem_percent_16
wilcoxon_test_results = pingouin.wilcoxon(
						x=sample_dem_data['dem_percent_12'], 
						y=sample_dem_data['dem_percent_16'], 
						alternative='two-sided')

# Print Wilcoxon test results
print(wilcoxon_test_results)
>>           W-val  alternative      p-val    RBC   CLES 
>>Wilcoxon  2401.0    two-sided  1.780e-77  0.962  0.645
```
