In the last few exercises, you looked at relationships between the sampling distribution and the bootstrap distribution. One way to quantify these distributions is the idea of "values within one standard deviation of the mean", which gives a good sense of where most of the values in a distribution lie. In this final lesson, we'll formalise the idea of values close to a statistic by defining the term "confidence interval".
## Predicting the weather
Consider meteorologists predicting weather in one of the world's most unpredictable regions - the northern Great Plains of the US and Canada. Rapid City, South Dakota was ranked as the least predictable of the 120 US cities with a National Weather Service forecast office. Suppose we've taken a job as a meteorologist at a news station in Rapid City. Our job is to predict tomorrow's high temperature.

We analyse the weather data using the best forecasting tools available to us and predict a high temperature of 47 degrees Fahrenheit. In this case, 47 degrees is our point estimate. Since the weather is variable, and many South Dakotans will plan their day tomorrow based on our forecast, we'd instead like to present a range of plausible values for the high temperature. On our weather show, we report that the high temperature will be between 40 and 54 degrees tomorrow.

This prediction of 40 to 54 degrees can be thought of as a confidence interval for the unknown quantity of tomorrow's high temperature. Although we can't be sure of the exact temperature, we are confident that it will be in that range. These results are often written as the point estimate followed by the confidence interval's lower and upper bounds in parentheses or square brackets. `47 F (40F,54F)` or `47F [40F,54F]`. When the confidence interval is symmetric around the point estimate, we can represent it as the point estimate plus or minus the margin of error, in this case, seven degrees, `47 ± 7F`.
## Bootstrap distribution of mean flavour
Here's the bootstrap distribution of the mean flavour from the coffee dataset.
```Python
import matplotlib.pyplot as plt
plt.hist(coffee_boot_distn, bins=15)
plt.show()
```
We can calculate the mean of these resampled mean flavours.
```Python
import numpy as np
np.mean(coffee_boot_distn)
>>7.513452892
```
If we create a confidence interval by adding and subtracting one standard deviation from the mean, we see that there are lots of values in the bootstrap distribution outside of this one standard deviation confidence interval.
```Python
np.mean(coffee_boot_distn) - np.std(coffee_boot_distn, ddof=1)
>>7.497385709174466

np.mean(coffee_boot_distn) + np.std(coffee_boot_distn, ddof=1)
>>7.529520074825534
```
## Quantile method for confidence intervals
If we want to include 95% of the values in the confidence interval, we can use quantiles. Recall that quantiles split distributions into sections containing a particular proportion of the total data. To get the middle 95% of values, we go from the 0.025 quantile to the 0.975 quantile since the difference between those two numbers is 0.95. To calculate the lower and upper bounds for this confidence interval, we call `np.quantile()` from NumPy, passing the distribution values and the quantile values to use. 
```Python
np.quantile(coffee_boot_distn, 0.025)
>>7.4817195

np.quantile(coffee_boot_distn, 0.975)
>>7.5448805
```
The confidence interval is from around 7.48 to 7.54.
## Inverse cumulative distribution function
There is a second method to calculate confidence intervals. To understand it, we need to be familiar with the normal distribution's inverse cumulative distribution function. The bell curve we've seen before is the probability density function or PDF. Using calculus, if we integrate this, we get the cumulative distribution function or CDF. If we flip the x and y axes, we get the inverse CDF. 

We can use `scipy.stats` and call `norm.ppf()` to get the inverse CDF. It takes a quantile between zero and one and returns the values of the normal distribution for that quantile. The parameters of loc and scale are set to 0 and 1 by default, corresponding to the standard normal distribution. 
```Python
from scipy.stats import norm
norm.ppf(quantile, loc=0, scale=1)
```
Notice that the values corresponding to 0.025 and 0.975 are about -2 and 2 for the standard normal distribution.
## Standard error method for confidence interval
This second method for calculating a confidence interval is called the standard error method. First, we calculate the point estimate, which is the mean of the bootstrap distribution, and the standard error, which is estimated by the standard deviation of the bootstrap distribution. 
```Python
point_estimate = np.mean(coffee_boot_distn)
>>7.513452892

std_error = np.std(coffee_boot_distn, ddof=1)
>>0.016067182825533724
```
Then we call norm.ppf to get the inverse CDF of the normal distribution with the same mean and standard deviation as the bootstrap distribution. 
```Python
from scipy.stats import norm
lower = norm.ppf(0.025, loc=point_estimate, scale=std_error)
upper = norm.ppf(0.975, loc=point_estimate, scale=std_error)
print((lower, upper))
>>(7.481961792328933, 7.544943991671067)
```
Again, the confidence interval is from 7.48 to 7.54, though the numbers differ slightly from last time since our bootstrap distribution isn't perfectly normal.
## Let's practice!
Let's calculate some confidence intervals!