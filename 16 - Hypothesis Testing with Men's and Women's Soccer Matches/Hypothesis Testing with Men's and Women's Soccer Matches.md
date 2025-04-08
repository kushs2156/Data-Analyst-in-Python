![[Pasted image 20250318183131.png]]
You're working as a sports journalist at a major online sports media company, specialising in soccer analysis and reporting. You've been watching both men's and women's international soccer matches for a number of years, and your gut instinct tells you that more goals are scored in women's international football matches than men's. This would make an interesting investigative article that your subscribers are bound to love, but you'll need to perform a valid statistical hypothesis test to be sure!

While scoping this project, you acknowledge that the sport has changed a lot over the years, and performances likely vary a lot depending on the tournament, so you decide to limit the data used in the analysis to only official `FIFA World Cup` matches (not including qualifiers) since `2002-01-01`.

You create two datasets containing the results of every official men's and women's international football match since the 19th century, which you scraped from a reliable online source. This data is stored in two CSV files: `women_results.csv` and `men_results.csv`.

The question you are trying to determine the answer to is:

> Are more goals scored in women's international soccer matches than men's?

You assume a **10% significance level**, and use the following null and alternative hypotheses:

 - $H_0$: The mean number of goals scored in women's international soccer matches is the same as men's.
 - $H_A$: The mean number of goals scored in women's international soccer matches is greater than men's.

For this analysis, you'll use Official `FIFA World Cup` matches since `2002-01-01`, and you'll also assume that each match is fully independent, i.e., team form is ignored.

The p-value and the result of the test _must_ be stored in a dictionary called `result_dict` in the form:

`result_dict = {"p_val": p_val, "result": result}`

where `p_val` is the p-value and `result` is either the string `"fail to reject"` or `"reject"`, depending on the result of the test.

```Python
# Start your code here!
import pandas as pd
import numpy as np
import pingouin
import matplotlib.pyplot as plt
```
```Python
men = pd.read_csv('men_results.csv')
women = pd.read_csv('women_results.csv')
```
```Python
men.head()
women.head()
```
Using `.head()` on both datasets shows that data includes matches from 1969 for women and 1872 for men. Also, it includes data for other tournaments when our focus is purely on the World Cup. We will start with a filtered version of both datasets to just include World Cup matches and matches since `2002-01-01`. This will mean filtering on rows where `tournament` is equal to `FIFA World Cup`.
```Python
men_filtered = men[(men['tournament'] == "FIFA World Cup") & \
			  (men['date'] > '2002-01-01')]

women_filtered = women[(women['tournament'] == 'FIFA World Cup') & \
				(women['date'] > '2002-01-01')]
```
The goals scored in each match is currently stored in two separate columns. We can simply add these together and store the total for each each match in a new column.
```Python
men_filtered['total_score'] = men_filtered['home_score'] + 
							  men_filtered['away_score']

women_filtered['total_score'] = women_filtered['home_score'] + 
								women_filtered['away_score']
```
Let's just do a quick calculation to see the mean number of goals per match for both tables.
```Python
mean_score_men = men_filtered['total_score'].mean()
>>2.5130208333333335

women_filtered['total_score'].mean()
>>2.98
```

---
## Standardising the test statistic
z-scores are calculated by taking the sample statistic, subtracting the mean of this statistic as the population parameter of interest, then dividing by the standard error. In the two sample case, the test statistic, denoted $t$, uses a similar equation. We take the difference between the sample statistics for the two groups, subtract the population difference between the two groups, then divide by the standard error.
$$
\begin{align}
t &= \frac{difference \, in \, sample \, stats - difference \, in \, population \, parameters}{standard error} \\
t &= \frac{(\bar{x}_{women}-\bar{x}_{men})-(\mu_{women}-\mu_{men})}{SE(\bar{x}_{women}-\bar{x}_{men})}
\end{align}
$$
## Standard error
To calculate the standard error, needed for the denominator of the test statistic equation, bootstrapping tends to be a good option. However, there is an easier way to approximate it. We calculate the standard deviation of the numeric variable for each group in the sample, and the number of observations in each group. Then enter those values into the equation and compute the result.
$$
SE(\bar{x}_{women}-\bar{x}_{men}) \approx \sqrt{\frac{s^2_{women}}{n_{women}} + \frac{s^2_{men}}{n_{men}}}
$$
- $s$ is the standard deviation of the variable
- $n$ is the sample size (number of observations/rows in sample)
## Assuming the null hypothesis is true
Here's the test statistic equation again. If we assume that the null hypothesis is true, there's a simplification we can make. The null hypothesis assumes that the population means are equal, and their difference is zero, so the population term in the numerator disappears. 
$$
H_{0}: \mu_{women} - \mu_{men} = 0 \rightarrow t = \frac{(\bar{x}_{women} - \bar{x}_{men})}{SE(\bar{x}_{women}-\bar{x}_{men})}
$$
Inserting the approximation for the standard error, we now have a way of calculating the test statistic using only calculations on the sample dataset.
$$
t = \frac{(\bar{x}_{women} - \bar{x}_{men})}{\sqrt{\frac{s^2_{women}}{n_{women}} + \frac{s^2_{men}}{n_{men}}}}
$$
We need the mean, standard deviation, and number of observations for each group to fill in the formula for t. We again use `.groupby()` and method combinations with mean, std, and count.

---

So far we have calculated the values for $\bar{x}_{women}$ and $\bar{x}_{men}$. We know need to calculate the standard deviation and sample size for each variable in order to reach a value for t.
```Python
women_std = women_filtered['total_score'].std()
>>2.022387265401036

men_std = men_filtered['total_score'].std()
>>1.6525436488378111

n_women = len(women_filtered['total_score'])
>>200

n_men = len(men_filtered['total_score'])
>>384
```
We now have everything we need to calculate a value for t.
```Python
numerator = mean_score_women - mean_score_men
denominator = np.sqrt(women_std ** 2/n_women + men_std**2/n_men)

t_value = numerator / denominator
>>2.812822759620731
```

Before we go from this t-value, we first need to first consider the degrees of freedom:
$$
df = n_{women} + n_{men} - 2
$$
```Python
degrees_of_freedom = n_women + n_men - 2
>>582
```

Now, we can finally use the t-distribution to calculate a p-value and conclude if we reject the null hypothesis or fail to reject it. Since the alternative hypothesis states that it wants to find if women's soccer matches on average have more goals than men's, we will conduct a right-tailed hypothesis test.

```Python
from scipy.stats import t
```
```Python
p_val = 1 - t.cdf(t_value, df=degrees_of_freedom)
>>0.0025383186141713088
```

Finally! As this p-value is below the set significance level of 10%, we can reject the null hypothesis and say that women's soccer games consist of more goals than men's' games in the FIFA World Cup. In order to submit this project, we have to submit the p-value and outcome of the hypothesis test in a dictionary.
- `result_dict = {"p_val": p_val, "result": result}`
```Python
result = "reject"

result_dict = {"p_val": p_val,
			   "result": result}
```

Okay, all wrong!!
Need to consider the assumptions to see if we use parametric or non-parametric tests.
```Python
men_filtered['total_score'].hist()
plt.title("Statistics of men")
plt.xlabel("Total number of goals scored in matches.")
plt.ylabel("Matches have been played with the same number of goals")
plt.show()
```
![[Pasted image 20250318201502.png]]
```Python
women_filtered['total_score'].hist()
plt.title("Statistic of women")
plt.xlabel("Total number of goals score in matches.")
plt.ylabel("Matches have been played with the same number of goals")
plt.show()
```
![[Pasted image 20250318201605.png]]

As we can see, neither of these distributions are normal, breaking one of the assumptions need for us to conduct parametric tests. Therefore, we must use a non-parametric test. In this case, we will conduct a Wilcoxon-Mann-Whitney test as we are working with unpaired data and want to work out if there truly is a statistical significant difference between the two variables.
```Python
results_overall = pingouin.mwu(x=women_filtered['total_score'],
					           y=men_filtered['total_score'],
				               alternative="greater")

p_val = results_overall['p-val'].iloc[0]
>>0.005106609825443641
```

As this p-value is lower than the significance level, we decide to reject the null hypothesis.

```Python
result = "reject"

result_dict = {"p_val": p_val,
               "result": result}
```

