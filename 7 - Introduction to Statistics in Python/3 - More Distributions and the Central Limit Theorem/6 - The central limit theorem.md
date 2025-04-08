Now that you're familiar with the normal distribution, it's time to learn about what makes it so important.
## Rolling a die 5 times
Let's go back to our dice rolling example. We have a Series of the numbers 1 to 6 called die. To simulate rolling the die 5 times, we'll call `die.sample`(). We pass in the Series we want to sample from, the size of the sample, and set replace to True. This gives us the results of 5 rolls. 
```Python
die = pd.Series([1, 2, 3, 4, 5, 6])
# Roll 5 times
samp_5 = die.sample(5, replace=True)
print(samp_5)
>>array([3, 1, 4, 1, 1])

np.mean(samp_5)
>>2.0
```
Now, we'll take the mean of the 5 rolls, which gives us 2.

If we roll another 5 times and take the mean, we get a different mean. If we do it again, we get another mean. Let's repeat this 10 times: we'll roll 5 times and take the mean. To do this, we'll use a for loop. We start by creating an empty list called sample_means to hold our means. We loop from 0 to 9 so that the process is repeated 10 times. Inside the loop, we roll 5 times and append the sample's mean to the sample_means list. This gives us a list of 10 different sample means. 
```Python
sample_means = []
for i in range(10):
	samp_5 = die.sample(5, replace=True)
	sample_means.append(np.mean(samp_5))
print(sample_means)
>>[3.8, 4.0, 3.8, 3.6, 3.2, 4.8, 2.6, 3.0, 2.6, 2.0]
```
Let's plot these sample means.
A distribution of a summary statistic like this is called a **sampling distribution**. This distribution, specifically, is a sampling distribution of the sample mean.

Now let's do this 100 times. If we look at the new sampling distribution, its shape somewhat resembles the normal distribution, even though the distribution of the die is uniform. Let's take 1000 means. This sampling distribution more closely resembles the normal distribution.
## Central Limit Theorem
This phenomenon is known as the central limit theorem, which states that a sampling distribution will approach a normal distribution as the number of trials increases. In our example, the sampling distribution became closer to the normal distribution as we took more and more sample means. It's important to note that the central limit theorem only applies when samples are taken randomly and are independent, for example, randomly picking sales deals with replacement.
## Standard deviation and the CLT
The central limit theorem, or CLT, applies to other summary statistics as well. If we take the standard deviation of 5 rolls 1000 times, the sample standard deviations are distributed normally, centred around 1.9, which is the distribution's standard deviation.
```Python
sample_sds = []
for i in range(1000):
	sample_sds.append(np.std(die.sample(5, replace=True)))
```
Another statistic that the CLT applies to is proportion. Let's sample from the sales team 10 times with replacement and see how many draws have Claire as the outcome. In this case, 10% of draws were Claire. If we draw again, there are 40% Claires. If we repeat this 1000 times and plot the distribution of the sample proportions, it resembles a normal distribution centred around 0.25, since Claire's name was on 25% of the tickets.
## Mean of sampling distribution
Since these sampling distributions are normal, we can take their mean to get an estimate of a distribution's mean, standard deviation, or proportion. If we take the mean of our sample means from earlier, we get 3.48. That's pretty close to the expected value, which is 3.5! Similarly, the mean of the sample proportions of Claires isn't far off from 0.25. In these examples, we know what the underlying distributions look like, but if we don't, this can be a useful method for estimating characteristics of an underlying distribution. The central limit theorem also comes in handy when you have a huge population and don't have the time or resources to collect data on everyone. Instead, you can collect several smaller samples and create a sampling distribution to estimate what the mean or standard deviation is.
## Let's practice!
Now, it's time to practice utilising the central limit theorem.