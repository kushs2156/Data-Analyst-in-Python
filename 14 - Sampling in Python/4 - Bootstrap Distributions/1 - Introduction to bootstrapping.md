So far, we've mostly focused on the idea of sampling without replacement. Sampling without replacement is like dealing a pack of cards. When we deal the ace of spades to one player, we can't then deal the ace of spades to another player. Sampling with replacement is like rolling dice. If we roll a six, we can still get a six on the next roll. Sampling with replacement is sometimes called resampling. We'll use the terms interchangeably.
## Simple random sample without replacement
If we take a simple random sample without replacement, each row of the dataset, or each type of coffee, can only appear once in the sample.
## Simple random sample with replacement
If we sample with replacement, it means that each row of the dataset, or each coffee, can be sampled multiple times.
## Why sample with replacement?
So far, we've been treating the coffee_ratings dataset as the population of all coffees. Of course, it doesn't include every coffee in the world, so we could treat the coffee dataset as just being a big sample of coffees. To imagine what the whole population is like, we need to approximate the other coffees that aren't in the dataset. Each of the coffees in the sample dataset will have properties that are representative of the coffees that we don't have. Resampling lets us use the existing coffees to approximate those other theoretical coffees.
## Coffee data preparation
To keep it simple, let's focus on three columns of the coffee dataset. To make it easier to see which rows ended up in the sample, we'll add a row index column called index using the reset_index method.
```Python
coffee_focus = coffee_ratings[["variety", "country_of_origin",
							   "flavor"]]
coffee_focus = coffee_focus.reset_index()
```
## Resampling with `.sample()`
To sample with replacement, we call sample as usual but set the replace argument to True. Setting frac to 1 produces a sample of the same size as the original dataset.
```Python
coffee_resamp = coffee_focus.sample(frac=1, replace=True)
```
Counting the values of the index column shows how many times each coffee ended up in the resampled dataset. Some coffees were sampled four or five times.
```Python
coffee_resamp['index'].value_counts()
```
That means that some coffees didn't end up in the resample. By taking the number of distinct index values in the resampled dataset, using len on drop_duplicates, we see that 868 different coffees were included. By comparing this number with the total number of coffees, we can see that 470 coffees weren't included in the resample.
```Python
num_unique_coffees = len(coffee_resamp.drop_duplicates(subset="index"))
>>868

len(coffee_ratings) - num_unique_coffees
>>470
```
## Bootstrapping
We're going to use resampling for a technique called bootstrapping. In some sense, bootstrapping is the opposite of sampling from a population. With sampling, we treat the dataset as the population and move to a smaller sample. With bootstrapping, we treat the dataset as a sample and use it to build up a theoretical population. A use case of bootstrapping is to try to understand the variability due to sampling. This is important in cases where we aren't able to sample the population multiple times to create a sampling distribution.
## Bootstrapping process
The bootstrapping process has three steps. First, randomly sample with replacement to get a resample the same size as the original dataset. Then, calculate a statistic, such as a mean of one of the columns. Note that the mean isn't always the choice here and bootstrapping allows for complex statistics to be computed, too. Then, replicate this many times to get lots of these bootstrap statistics. Earlier in the course, we did something similar. We took a simple random sample, then calculated a summary statistic, then repeated those two steps to form a sampling distribution. This time, when we've used resampling instead of sampling, we get a **bootstrap distribution**.
## Bootstrapping coffee mean flavour
The resampling step uses the code we just saw: calling sample with frac set to one and replace set to True. Calculating a bootstrap statistic can be done with mean from NumPy. In this case, we're calculating the mean flavour score. To repeat steps one and two one thousand times, we can wrap the code in a for loop and append the statistics to a list.
```Python
import numpy as np
mean_flavors_1000 = []
for i in range(1000):
	mean_flavors_1000.append(
		np.mean(coffee_sample.sample(frac=1, replace=True)['flavor'])
	)
```
Here's a histogram of the bootstrap distribution of the sample mean. Notice that it is close to following a normal distribution.
```Python
import matplotlib.pyplot as plt
plt.hist(mean_flavors_1000)
plt.show()
```
## Let's practice!
Best get bootstrapping.