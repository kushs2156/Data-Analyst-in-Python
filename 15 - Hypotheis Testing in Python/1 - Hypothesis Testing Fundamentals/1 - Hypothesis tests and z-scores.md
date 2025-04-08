Hi, I'm James. Welcome to this course on hypothesis testing in Python. To start, let's look at a real-world example where a hypothesis test was crucial in a decision-making process.
## A/B testing
In 2013, Electronic Arts, or EA, launched a video game called SimCity 5. Leading up to its release, they wanted to increase pre-order sales. They used an experimental design technique called A/B testing, which has roots in hypothesis testing, to test different advertising scenarios and see which improved sales the most. Website visitors were split into a control group and a treatment group. Each group saw a different version of the game's pre-order sales page.

Here's each version of the SimCity 5 pre-order page. The control group saw the version with a banner advertising money off their next purchase with each pre-order. The treatment group saw the version without the banner. EA compared the percentage of checkouts for the two groups to see which performed best. Our naïve guess would be that the advertisement increased pre-order sales.

The results of the A/B test were surprising. The treatment page without the advertisement resulted in 43% higher sales than the control page with the advert. The experiment proved that our intuition that more discount adverts would result in more sales was false. We might ask ourselves, was the 43% difference a meaningful difference between the control and treatment groups, or was it just random chance? To get this answer, we'd need the original dataset from EA, which isn't publicly available. However, the method to answering this question of significance would involve techniques from both the Sampling in Python course and from this course.
## Stack Overflow Developer Survey 2020
Each year, Stack Overflow surveys its users, who are primarily software developers, about themselves, how they use Stack Overflow, their work, and the development tools they use. In this course, we'll look at a subset of the survey responses from users who identified as Data Scientists.
## Hypothesising about the mean
Let's hypothesise that the mean annual compensation of the population of data scientists is $110,000. We can initially examine the mean annual compensation from the sample survey data. Annual compensation, converted to dollars, is stored in the converted_comp column. The sample mean is a type of point estimate, which is another name for a summary statistic. We can calculate it with pandas using the .mean method on the converted_comp Series. The result is different from our hypothesis, but is it meaningfully different?
```Python
mean_comp_samp = stack_overflow['converted_comp'].mean()
>>119574.71738168952
```
## Generating a bootstrap distribution
To answer this, we need to generate a bootstrap distribution of sample means. This is done by resampling the dataset, calculating the sample mean for that resample, then repeating those steps to create a list of sample means.
```Python
import numpy as np
# Step 3. Repeat steps 1 & 2 many times, appending to a list
so_boot_distn = []
for i in range(5000):
	so_boot_distn.append(
		# Step 2. Calculate point estimate
		np.mean(
			# Step 1. Resample
			stack_overflow.sample(frac=1, replace=True)\
			['converted_comp']
		)
	)
```
Here's a histogram of the bootstrap distribution. Its bell shape means that it's roughly normally distributed. Notice that 110,000 is on the left of the distribution.
```Python
import matplotlib.pyplot as plt
plt.hist(so_boot_distn, bins=50)
plt.show()
```
## Standard error
Recall that the standard deviation of the sample statistics in the bootstrap distribution estimates the standard error of the statistic.
```Python
std_error = np.std(so_boot_distn, ddof=1)
>>5607.997577378606
```
## z-scores
Since variables have arbitrary units and ranges, before we test our hypothesis, we need to standardise the values. A common way of standardising values is to subtract the mean, and divide by the standard deviation. 
$$
standardized \, value = \frac{value - mean}{standard \, deviation}
$$
For hypothesis testing, we use a variation where we take the sample statistic, subtract the hypothesised parameter value, and divide by the standard error. The result is called a z-score.
$$
z = \frac{sample \, stat - hypoth. \, param\, value}{standard \, error}
$$
Here are the values we calculated earlier. The sample mean annual compensation for data scientists of around $120,000, minus the hypothesised compensation of $110,000, divided by the standard error gives a z-score of 1.707.
```Python
z_score = (mean_comp_samp - mean_comp_hyp) / std_error
```
## Testing the hypothesis
Is that a big or small number? Determining that is the goal of this course. In particular, we can now state one of the uses of hypothesis testing: determining whether a sample statistic is close to or far away from an expected value.
## Standard normal (z) distribution
One final thing. Here's a plot of the probability density function for the standard normal distribution, which is a normal distribution with mean of zero and standard deviation of one. It's often called the z-distribution, and z-scores are related to this distribution. We'll encounter the z-distribution throughout this course.
## Let's practice!
Time to begin!