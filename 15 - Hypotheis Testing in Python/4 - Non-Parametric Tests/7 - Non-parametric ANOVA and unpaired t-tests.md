In the previous video, we explored some non-parametric techniques and how they compare to their parametric counterparts. We'll continue on that theme here focusing on non-parametric alternatives to tests of independent numeric samples.
## Wilcoxon-Mann-Whitney test
We can avoid assumptions about normally distributed data by performing hypothesis tests on the ranks of a numeric input. The Wilcoxon-Mann-Whitney test is, very roughly speaking, a t-test on ranked data. This test is similar to the Wilcoxon test we saw in the last video, but works on unpaired data instead.

Let's return to the Stack Overflow survey and the relationship between converted compensation and the age respondents began coding. We start by focusing on just those two columns in a new DataFrame called age_vs_comp. 
```Python
age_vs_comp = stack_overflow[['converted_comp', 'age_first_code_cut']]
```
To conduct a Wilcoxon-Mann-Whitney test with pingouin, we first need to convert our data from long to wide format. This is accomplished with the pivot method from pandas, which unlike pivot_table, does not aggregate; instead, it returns the raw values for each group across the rows. 
```Python
age_vs_comp_wide = age_vs_comp.pivot(columns='age_first_code_cut',
									 values='converted_comp')
```
We now have our data in two columns named adult and child with the values corresponding to the converted_comp entries for each row. An adult value of `NaN` corresponds to a child entry and a child value of `NaN` corresponds to an adult entry.

Let's set a significance level of 1%. We can run a Wilcoxon-Mann-Whitney test using `mwu` from pingouin. It accepts x and y arguments corresponding to the two columns of numbers we want to compare, in this case, child and adult. alternative sets the type of alternative hypothesis, in this case, that those who code first as children have a higher income than those who code first as adults, which is a right-tailed test. 
```Python
import pingouin
pingouin.mwu(x=age_vs_comp_wide['child'],
			 y=age_vs_comp_wide['adult'],
			 alternative='greater')
```
Here, the p-value is shown as around $1.9 \times 10^{-19}$, which is significantly smaller than the significance level.
## Kruskal-Wallis test
In the same way that ANOVA extends t-tests to more than two groups, the Kruskal-Wallis test extends the Wilcoxon-Mann-Whitney test to more than two groups. That is, the Kruskal-Wallis test is a non-parametric version of ANOVA. We use the `kruskal()` method from pingouin to perform a Kruskal-Wallis test to investigate if there is a difference in converted_comp between job satisfaction groups. Unlike the Wilcoxon-Mann-Whitney test, we don't need to pivot our data here since the kruskal method works on long data. We pass in stack_overflow as data, the dependent variable, dv, as converted_comp, and we are comparing between the groups of job_sat. 
```Python
alpha = 0.01

pingouin.kruskal(data=stack_overflow,
				 dv='converted_comp',
				 between='job_sat')
>>          Source  ddof1          H         p-unc
>>Kruskal  job_sat      4  72.814939  5.772915e-15
```
Again, the p-value here is very small and smaller than our significance level. This provides evidence that at least one of the mean compensation totals is different than the others across these five job satisfaction groups.
## Let's practice!
You're almost there! Head on over to the exercises to give these tests a go.