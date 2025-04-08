We just saw how point estimates like the sample mean will vary depending on which rows end up in the sample. For example, this same code to calculate the mean cup points from a simple random sample of thirty coffees gives a slightly different answer each time. Let's try to visualise and quantify this variation.

A for loop lets us run the same code many times. It's especially useful for situations like this where the result contains some randomness. We start by creating an empty list to store the means. Then, we set up the for loop to repeatedly sample 30 coffees from coffee_ratings a total of 1000 times, calculating the mean cup points each time. After each calculation, we append the result, also called a replicate, to the list. Each time the code is run, we get one sample mean, so running the code a thousand times generates a list of one thousand sample means.
```Python
mean_cup_points_1000 = []
for i in range(1000):
	mean_cup_points_1000.append(
		coffee_ratings.sample(n=30)['total_cup_points'].mean()
	)
print(mean_cup_points_1000)
```
## Distribution of sample means for size 30
The 1000 sample means form a distribution of sample means. To visualise a distribution, the best plot is often a histogram. Here we can see that most of the results lie between 81 and 83, and they roughly follow a bell-shaped curve, like a normal distribution. 
```Python
import matplotlib.pyplot as plt
plt.hist(mean_cup_points_1000, bins=30)
plt.show()
```
There's an important piece of jargon we need to know here. A distribution of replicates of sample means, or other point estimates, is known as a **sampling distribution**.
## Different sample sizes
Here are histograms from running the same code again with different sample sizes. When we decrease the original sample size of 30 to 6, we can see from the x-values that the range of the results is broader. The bulk of the results now lie between 80 and 84. On the other hand, increasing the sample size to 150 results in a much narrower range. Now most of the results are between 81.8 and 82.6. As we saw previously, bigger sample sizes give us more accurate results. By replicating the sampling many times, as we've done here, we can quantify that accuracy.
## Let's practice!
Ready to replicate?