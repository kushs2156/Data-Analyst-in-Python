- Conduct a t-test on the sample differences (the `diff` column of `sample_dem_data`), using an appropriate alternative hypothesis chosen from `"two-sided"`, `"less"`, and `"greater"`.
```Python
# Conduct a t-test on diff
test_results = pingouin.ttest(x=sample_dem_data['diff'], y=0, 
							  alternative="two-sided")

# Print the test results
print(test_results)
>>     T dof alternative      p-val        CI95%  
>>30.298 499   two-sided 3.601e-115 [6.39, 7.27]
```
- What's the correct decision from the t-test, assuming α=0.01?
Reject the null hypothesis
- Conduct a paired test on the democratic votes in 2012 and 2016 (the `dem_percent_12` and `dem_percent_16` columns of `sample_dem_data`), using an appropriate alternative hypothesis.
```Python
# Conduct a paired t-test on dem_percent_12 and dem_percent_16
paired_test_results = pingouin.ttest(
		x=sample_dem_data['dem_percent_12'],
		y=sample_dem_data['dem_percent_16'],
		paired=True,
		alternative='two-sided')
		
# Print the paired test results
print(paired_test_results)
>>            T dof alternative      p-val       CI95% 
>>T-test 30.298 499   two-sided 3.601e-115 [6.39, 7.27]
```
- Compare the paired t-test to an (inappropriate) unpaired test on the same data. How does the p-value change?
```Python
pingouin.ttest(x=sample_dem_data['dem_percent_12'],
			   y=sample_dem_data['dem_percent_16'],
			   alternative="two-sided")
```
The p-value from the unpaired test is greater than the p-value from the unpaired test.