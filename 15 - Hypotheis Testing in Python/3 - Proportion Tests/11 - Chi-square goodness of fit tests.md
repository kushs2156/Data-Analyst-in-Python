Last time, we used a chi-square test to compare proportions in two categorical variables. This time, we'll use another variant of the chi-square test to compare a single categorical variable to a hypothesised distribution.
## Purple links
The Stack Overflow survey contains a fun question about how users feel when they discover that they already visited the top resource, also called a purple link, when trying to solve a coding problem. We can use the `.value_counts()` method to get the counts of each group in the purple_link column. 
```Python
purple_link_counts = stack_overflow['purple_link'].value_counts()

purple_link_counts = purple_link_counts.rename_axis('purple_link')\
									   .reset_index(name='n')\
									   .sort_values('purple_link')
```
We also do a little bit of manipulation here to get a nicely structured DataFrame that we can work with later. First, we rename the leftmost column to be purple_link, assign the counts to n, and finally sort by purple_link, so the responses are in alphabetical order. There are four possible answers stored in the purple_link column.
## Declaring the hypotheses
Let's hypothesise that half of the users in the population would respond "Hello, old friend", and the other three responses would get 1/6 each. We can create a DataFrame for these hypothesised results from a dictionary of key-value pairs for each response. 
```Python
hypothesized = pd.DataFrame({
	'purple_link': ['Amused', 'Annoyed', 'Hello, old friend',
					'Indifferent'],
	'prop': [1/6, 1/6, 1/2, 1/6]})
```
We specify the hypotheses as whether or not the sample matches this hypothesised distribution. The test statistic, chi-squared, measures how far the observed sample distribution of proportions is from the hypothesised distribution. Let's set the significance level of 0.01.
- $H_0$: The sample matches the hypothesised distribution
- $H_A$: The sample does not match the hypothesised distribution
## Hypothesised counts by category
To visualise the purple_link distribution, it will help to have the hypothesised counts for each answer, which are calculated by multiplying the hypothesised proportions by the total number of observations in the sample.
```Python
n_total = len(stack_overflow)
hypothesized["n"] = hypothesized["prop"] * n_total
```
## Visualising counts
Let's create a visualisation to see how well the hypothesised counts appear to model the observed counts. The natural way to visualise the counts of a categorical variable is with a bar plot. First, we use plt.bar to plot the observed purple_link counts, setting the horizontal axis to purple_link and the vertical axis to n. We set the colour of the bars and add a label for a legend. We do the same again for the hypothesised counts, but also add transparency with the alpha argument.
```Python
import matplotlib.pyplot as plt

plt.bar(purple_link_counts['purple_link'], purple_link_counts['n'],
		color='red', label='Observed')
plt.bar(hypothesized['purple_link'], hypothesized['n'], alpha=0.5,
		color='blue', label='Hypothesized')

plt.legend()
plt.show()
```
We can see that two of the responses are reasonably well-modeled by the hypothesised distribution and another two appear quite different, but we'll need to run a hypothesis test to see if the difference is statistically significant.
## chi-square goodness of fit test
The one-sample chi-square test is called a goodness of fit test, as we're testing how well our hypothesised data fits the observed data. To run the test, we use the `chisquare()` method from scipy.stats. There are two required arguments to chisquare: an array-like object for the observed counts, f_obs, and one for the expected counts, f_exp. 
```Python
from scipy.stats import chisquare
chisquare(f_obs=purple_link_counts['n'], f_exp=hypothesized['n'])
>>Power_divergenceResult(statistic=44.59840778416629,
>>pvalue=1.1261810719413759e-09)
```
The p-value returned by the function is very small, much lower than the significance level of 0.01, so we conclude that the sample distribution of proportions is different from the hypothesised distribution.
## Let's practice!
Let's perform some chi-square goodness of fit tests.