We've seen how to compare two groups in the unpaired and paired cases. But what if there are more than two groups? The Stack Overflow survey includes a job satisfaction variable, with five categories from "Very satisfied" down to "Very dissatisfied". Suppose we want to know if mean annual compensation is different for each of the levels of job satisfaction. The first thing to do is visualise the distributions with box plots. Seaborn's boxplot method provides a nice option here with converted_comp on the horizontal axis and job_sat on the vertical axis using the stack_overflow data. "Very satisfied" looks slightly higher than the others, but to see if they are significantly different, we'll need to use hypothesis tests.
```Python
import seaborn as sns
import matplotlib.pyplot as plt
sns.boxplot(x="converted_comp", y="job_sat",
			data=stack_overflow)
plt.show()
```
## Analysis of variance (ANOVA)
ANOVA tests determine whether there are differences between the groups. We begin by setting our significance level to 0.2. This value is larger than in many situations but will help us understand the implications on comparing different numbers of groups later on. We use the `pingouin.anova()` method to compare values across multiple groups. We specify the data as stack_overflow, the dependent variable, `dv`, as converted_comp, and the column of groups to calculate between as job_sat. 
```Python
alpha = 0.2

pingouin.anova(data=stack_overflow,
			   dv='converted_comp', between='job_sat')
>>    Source  ddof1  ddof2         F     p-unc       np2
>>0  job_sat      4   2256  4.480485  0.001315  0.007882
```
The p-value is stored in the `p-unc` column, which is 0.0013, which is smaller than alpha at 20%. That means that at least two of the categories of job satisfaction have significant differences between their compensation levels, but this doesn't tell us which two categories they are.
## Pairwise tests
To identify which categories are different, we compare all five job satisfaction categories, testing on each pair in turn. There are ten ways of choosing two items from a set of five, so we have ten tests to perform. Our significance level is still 0.2.
- $\mu_{very \, dissatisfied} \neq \mu_{slightly \, dissatisfied}$
- $\mu_{very \, dissatisfied} \neq \mu_{neither}$
- $\mu_{very \, dissatisfied} \neq \mu_{slightly \, satisfied}$
- $\mu_{very \, dissatisfied} \neq \mu_{very \, ssatisfied}$
- $\mu_{slightly \, dissatisfied} \neq \mu_{neither}$
- $\mu_{slightly \, dissatisfied} \neq \mu_{slightly \, satisfied}$
- $\mu_{slightly \, dissatisfied} \neq \mu_{very \, satisfied}$
- $\mu_{neither} \neq \mu_{slightly \, satisfied}$
- $\mu_{neither} \neq \mu_{very \, satisfied}$
- $\mu_{slightly \, satisfied} \neq \mu_{very \, satisfied}$
## `pairwise_tests()`
To run all these hypothesis tests in one go, we can use `.pairwise_tests()`. The first three arguments of data, dv, and between are the same as the anova method. We'll discuss `padjust` shortly. 
```Python
pingouin.pairwise_tests(data=stack_overflow,
						dv="converted_comp",
						between="job_sat",
						padjust="none")
```
The result shows a DataFrame where A and B are the two levels being compared on each row. Next, we look at the p-unc column of p-values. Three of these are less than our significance level of point-two.
## As the number of groups increases...
In this case we have five groups, resulting in ten pairs. As the number of groups increases, the number of pairs - and hence the number of hypothesis tests we must perform - increases quadratically. The more tests we run, the higher the chance that at least one of them will give a false positive significant result. With a significance level of 0.2, if we run one test, the chance of a false positive result is 0.2. With five groups and ten tests, the probability of at least one false positive is around 0.7. With twenty groups, it's almost guaranteed that we'll get at least one false positive.
## Bonferroni correction
The solution to this is to apply an adjustment to increase the p-values, reducing the chance of getting a false positive. One common adjustment is the Bonferroni correction. Looking at the p-corr column corresponding to corrected p-values, as opposed to the p-unc column for uncorrected, only two of the pairs appear to have significant differences.
```Python
pingouin.pairwise_tests(data=stack_overflow,
						dv="converted_comp",
						between="job_sat",
						padjust="bonf")
```
## More methods
pingouin provides several options for adjusting the p-values with some being more conservative than others. No adjustment with none is the default, but in almost all pairwise t-testing situations choosing a correction method is more appropriate.
- `none`: no correction \[default]
- `bonf`: one-step Bonferroni correction
- `sidak`: one-step Sidak correction
- `holm`: step-down method using Bonferroni adjustments
- `fdr_bh`: Benjamini/Hochberg FDR correction
- `fdr_by`: Benjamini/Yekutielo FDR correction
## Let's practice!
Let's run lots of tests.