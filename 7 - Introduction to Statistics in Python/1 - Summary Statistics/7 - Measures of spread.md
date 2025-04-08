In this lesson, we'll talk about another set of summary statistics: measures of spread. Spread is just what it sounds like - it describes how spread apart or close together the data points are. Just like measures of centre, there are a few different measures of spread.
## Variance
The first measure, variance, measures the average distance from each data point to the data's mean. To calculate the variance, we start by calculating the distance between each point and the mean, so we get one number for every data point. We then square each distance and then add them all together.
```Python
dists = msleep['sleep_total'] - np.mean(msleep['sleep_total'])

sq_dists = dists ** 2

sum_sq_dists = np.sum(sq_dists)

variance = sum_sq_dists / (83-1)
print(variance)
>>19.805677
```
Finally, we divide the sum of squared distances by the number of data points minus 1, giving us the variance. The higher the variance, the more spread out the data is. It's important to note that the units of variance are squared, so in this case, it's 19.8 hours squared. We can calculate the variance in one step using `np.var`, setting the `ddof` argument to 1. If we don't specify `ddof = 1`, a slightly different formula is used to calculate variance that should only be used on a full population, not a sample.
```Python
np.var(msleep['sleep_total'], ddof=1)
>>19.805677

np.var(msleep['sleep_total'])
>>19.567055
```
## Standard deviation
The standard deviation is another measure of spread, calculated by taking the square root of the variance. It can be calculated using `np.std`. Just like `np.var`, we need to set `ddof = 1`. The nice thing about standard deviation is that the units are usually easier to understand since they're not squared. It's easier to wrap your head around 4 and a half hours than 19.8 hours squared.
```Python
np.sqrt(np.var(msleep['sleep_total'], ddof=1))
>>4.450357

np.std(msleep['sleep_total'], ddof=1)
>>4.450357
```
## Mean absolute deviation
Mean absolute deviation takes the absolute value of the distances to the mean, and then takes the mean of those differences. 
```Python
dists = msleep['sleep_total'] - mean(msleep$sleep_total)
np.mean(np.abs(dists))
>>3.566701
```
While this is similar to standard deviation, it's not exactly the same. Standard deviation squares distances, so longer distances are penalized more than shorter ones, while mean absolute deviation penalizes each distance equally. One isn't better than the other, but SD is more common than MAD.
## Quantiles
Before we discuss the next measure of spread, let's quickly talk about quantiles. Quantiles, also called percentiles, split up the data into some number of equal parts. Here, we call `np.quantile`, passing in the column of interest, followed by 0.5. This gives us 10.1 hours, so 50% of mammals in the dataset sleep less than 10.1 hours a day, and the other 50% sleep more than 10.1 hours, so this is exactly the same as the median. 
```Python
np.quantile(msleep['sleep_total'], 0.5)
>>10.1

np.quantile(msleep['sleep_total'], [0, 0.25, 0.5, 0.75, 1])
>>array([ 1.9 , 7.85, 10.1 , 13.75, 19.9 ])
```
We can also pass in a list of numbers to get multiple quantiles at once. Here, we split the data into 4 equal parts. These are also called quartiles. This means that 25% of the data is between 1.9 and 7.85, another 25% is between 7.85 and 10.10, and so on.
## Boxplots use quartiles
The boxes in box plots represent quartiles. The bottom of the box is the first quartile, and the top of the box is the third quartile. The middle line is the second quartile, or the median.
```Python
import matplotlib.pyplot as plt
plt.boxplot(msleep['sleep_total'])
plt.show()
```
## Quantiles using `np.linspace()`
Here, we split the data in five equal pieces, but we can also use `np.linspace` as a shortcut, which takes in the starting number, the stopping number, and the number intervals. We can compute the same quantiles using `np.linspace` starting at zero, stopping at one, splitting into 5 different intervals.
```Python
np.quantile(msleep['sleep_total'], [0, 0.25, 0.5, 0.75, 1])
>>array([ 1.9 , 7.85, 10.1 , 13.75, 19.9 ])

np.quantile(msleep['sleep_total'], np.linspace(0, 1, 5))
>>array([ 1.9 , 7.85, 10.1 , 13.75, 19.9 ])
```
## Interquartile range (IQR)
The interquartile range, or IQR, is another measure of spread. It's the distance between the 25th and 75th percentile, which is also the height of the box in a boxplot. We can calculate it using the quantile function, or using the iqr function from `scipy.stats` to get 5.9 hours.
```Python
np.quantile(msleep['sleep_total'], 0.75) - np.quantile(msleep['sleep_total'], 0.25)
>>5.9

from scipy.stats import iqr
iqr(msleep['sleep_total'])
>>5.9
```
## Outliers
Outliers are data points that are substantially different from the others. But how do we know what a substantial difference is? A rule that's often used is that any data point less than the first quartile minus 1.5 times the IQR is an outlier, as well as any point greater than the third quartile plus 1.5 times the IQR.

To find outliers, we'll start by calculating the IQR of the mammals' body weights. We can then calculate the lower and upper thresholds following the formulas from the previous slide. We can now subset the DataFrame to find mammals whose body weight is below or above the thresholds. There are eleven body weight outliers in this dataset, including the cow and the Asian elephant.
```Python
from scipy.stats import iqr
iqr = iqr(msleep['bodywt'])
lower_threshold = np.quantile(msleep['bodywt'], 0.25) - 1.5 * iqr
upper_threshold = np.quantile(msleep['bodywt'], 0.75) + 1.5 * iqr

msleep[(msleep['sleep_total'] < lower_threshold) | 
	   (msleep['sleep_total'] > upper_threshold)]
```
## All in one go
Many of the summary statistics we've covered so far can all be calculated in just one line of code using the `.describe()` method, so it's convenient to use when you want to get a general sense of your data.
```Python
msleep.describe()
```
## Let's practice!
Time to practice measuring spread and finding outliers.