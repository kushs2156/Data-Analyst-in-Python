Just as ANOVA extends t-tests to more than two groups, chi-square tests of independence extend proportion tests to more than two groups. Here's the proportions test from the last video. The test statistic is the z-score of minus -4.22. That proportion test had a positive result. The small p-value suggested that there was evidence that the hobbyist and age category variables had an association. If the proportion of hobbyists was the same for each age category, the variables would be considered statistically independent. More formally, two categorical variables are consider **statistically independent** when the proportion of successes in the response variable is the same across all categories of the explanatory variable.
## Test for independence of variables
The pingouin package has an indirect way of testing the difference in the proportions from the previous video. To the `chi2_independence()` method, we pass stack_overflow as data, hobbyist as x, and age_cat as y. The correction argument specifies whether or not to apply Yates' continuity correction, which is a fudge factor for when the sample size is very small and the degrees of freedom is one. Since each group has over one hundred observations, we don't need it here. 
```Python
import pingouin
expected, observed, stats = pingouin.chi2_independence(\
							data=stack_overflow,
							x='hobbyist',
							y='age_cat',
							correction=False)
print(stats)
```
The method returns three different pandas DataFrames: the expected counts, the observed counts, and statistics related to the test. Let's look at stats and focus on the pearson test row and the chi2 and pval columns. The p-value is the same as we had with the z-test of around 0.000024. The chi2 value is the squared result of our z-score seen in the previous video.
- $\chi^2 \text{statistic} = 17.839570 = (-4.223691463320559)^2 = (z\text{-score})^2$
## Job satisfaction and age category
Let's try another example. Recall that the Stack Overflow sample has an age category variable with two categories and a job satisfaction variable with five categories. We can declare hypotheses to test for independence of these variables. Here, age category is the response variable, and job satisfaction is the explanatory variable. The null hypothesis is that independence occurs. Let's use a significance level of 0.1. The test statistic is denoted $\chi^2$. It quantifies how far away the observed results are from the expected values if independence was true.
- $H_0$: Age categories are independent of job satisfaction levels
- $H_A$: Age categories are not independent of job satisfaction levels
## Exploratory visualisation: proportional stacked bar plot
Let's explore the data using a proportional stacked bar plot. We begin by calculating the proportions in each age group. Next, we use the unstack method to convert this table into wide format. Using the plot method and setting kind to bar and stacked to True produces a proportional stacked bar plot.
```Python
props = stack_overflow.groupby('job_sat')['age_cat']\
					  .value_counts(normalize=True)

wide_props = props.unstack()
wide_props.plot(kind="bar", stacked=True)
```
If the age category was independent of job satisfaction, the split between the age categories would be at the same height in each of the five bars. There's some variation here, but we'll need a chi-square independence test to determine whether it's a significant difference.
## Chi-square independence test
Let's again use the chi-square independence test from pingouin. We have stack_overflow as the data and job_sat and age_cat as x and y. We leave out a correction here since our degrees of freedom is four, calculated by subtracting one from each of the variable categories and multiplying. 
- $(\text{No. of response categories} - 1) \times (\text{No. explanatory categories} - 1)$
- $(2 - 1) * (5 - 1) = 4$
```Python
import pingouin
expected, observed, stats = pingouin.chi2_independence(\
									 data=stack_overflow,
									 x="job_sat",
									 y="age_cat")
print(stats)
```
The p-value is 0.23, which is above the significance level we set, so we conclude that age categories are independent of job satisfaction.
## Swapping the variables?
Swapping the variables, so age category is the response and job satisfaction is the explanatory variable, we see that the splits for each bar are in similar places.
```Python
props = stack_overflow.groupby('age_cat')['job_sat']\
					  .value_counts(normalize=True)
wide_props = props.unstack()
wide_props.plot(kind="bar", stacked=True)
```
If we run the chi-square test with the variables swapped, then the results are identical. 
```Python
import pingouin
expected, observed, stats = pingouin.chi2_independence(\
									 data=stack_overflow,
									 x="age_cat",
									 y="job_sat")
print(stats[stats['test'] == 'pearson'])
```
Because of this, we phrase our questions as "are variables X and Y independent?", rather than "is variable X independent from variable Y?", since the order doesn't matter.
## What about direction and tails?
We didn't worry about tails in this test, and in fact, the chi2_independence method doesn't have an alternative argument. This is because the chi-square test statistic is based on the square of observed and expected counts, and square numbers are non-negative. That means that chi-square tests tend to be right-tailed tests.
## Let's practice!
Time for some practice!