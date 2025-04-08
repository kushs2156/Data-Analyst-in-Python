In the last video, we took a focused subset of the coffee dataset. Here's a five hundred row sample from it.
```Python
coffee_sample = coffee_ratings[["variety", "country_of_origin",
	"flavor"]].reset_index().sample(n=500)
```
Here, we generate a bootstrap distribution of the mean coffee flavour scores from that sample. .sample generates a resample, np.mean calculates the statistic, and the for loop with .append repeats these steps to produce a distribution of bootstrap statistics.
```Python
import numpy as np
mean_flavors_500 = []
for i in range(5000):
	mean_flavors_5000.append(
		np.mean(coffee_sample.sample(frac=1, replace=True)['flavor'])
	)
bootstrap_distn = mean_flavors_5000
```
Here's the histogram of the bootstrap distribution, which is close to a normal distribution.
```Python
import matplotlib.pyplot as plt
plt.hist(bootstrap_distn, bins=15)
plt.show()
```
## Sample, bootstrap distribution, population means
Here's the mean flavour score from the original sample. 
```Python
coffee_sample['flavor'].mean()
>>7.5132200000000005
```
In the bootstrap distribution, each value is an estimate of the mean flavour score. Recall that each of these values corresponds to one potential sample mean from the theoretical population. If we take the mean of those means, we get our best guess of the population mean. 
```Python
np.mean(bootstrap_distn)
>>7.513357731999999
```
The two values are really close. However, there's a problem. The true population mean is actually a little different.
```Python
coffee_ratings['flavor'].mean()
>>7.526046337817639
```
## Interpreting the means
The behaviour that you just saw is typical. The bootstrap distribution mean is usually almost identical to the original sample mean. However, that is not often a good thing. If the original sample wasn't closely representative of the population, then the bootstrap distribution mean won't be a good estimate of the population mean. Bootstrapping cannot correct any potential biases due to differences between the sample and the population.
## Sample sd vs. bootstrap distribution sd
While we do have that limitation in estimating the population mean, one great thing about distributions is that we can also quantify variation. The standard deviation of the sample flavours is around 0.354. 
```Python
# Sample standard deviation
coffee_sample['flavor'].std()
>>0.3540883911928703
```
Recall that pandas .std calculates a sample standard deviation by default. If we calculate the standard deviation of the bootstrap distribution, specifying a ddof of one, then we get a completely different number. 
```Python
# Standard error
np.std(bootstrap_distn, ddof=1)
>>0.015768474367958217
```
So what's going on here?
## Sample, bootstrap dist'n, pop'n standard deviations
Remember that one goal of bootstrapping is to quantify what variability we might expect in our sample statistic as we go from one sample to another. Recall that this quantity is called the standard error as measured by the standard deviation of the sampling distribution of that statistic. The standard deviation of the bootstrap means can be used as a way to estimate this measure of uncertainty. If we multiply that standard error by the square root of the sample size, we get an estimate of the standard deviation in the original population. 
```Python
standard_error * np.sqrt(500)
>>0.3525938058821761
```
Our estimate of the standard deviation is around 0.353. The true standard deviation is around 0.341, so our estimate is pretty close. In fact, it is closer than just using the sample standard deviation alone.
```Python
# True standard deviation
coffee_ratings['flavor'].std(ddof=0)
>>0.34125481224622645
```
## Interpreting the standard errors
To recap, the estimated standard error is the standard deviation of the bootstrap distribution values for our statistic of interest. This estimated standard error times the square root of the sample size gives a really good estimate of the standard deviation of the population. That is, although bootstrapping was poor at estimating the population mean, it is generally great for estimating the population standard deviation.
$$
Population \, std. \, dev \approx Std. \, Error \times \sqrt{Sample \, size}
$$
## Let's practice!
Let's play with some standard errors.