The point estimates you calculated in the previous exercises were very close to the population parameters that they were based on, but is this always the case?

In 1936, a newspaper called The Literary Digest ran an extensive poll to try to predict the next US presidential election. They phoned ten million voters and had over two million responses. About 1.3 million people said they would vote for Landon, and just under 1 million people said they would vote for Roosevelt. That is, Landon was predicted to get 57% of the vote, and Roosevelt was predicted to get 43% of the vote. Since the sample size was so large, it was presumed that this poll would be very accurate. However, in the election, Roosevelt won by a landslide with 62% of the vote. So what went wrong? Well, in 1936, telephones were a luxury, so the only people who had been contacted by The Literary Digest were relatively rich. The sample of voters was not representative of the whole population of voters, and so the poll suffered from sample bias. The data was collected by the easiest method, in this case, telephoning people. This is called convenience sampling and is often prone to sample bias. Before sampling, we need to think about our data collection process to avoid biased results.

Let's look at another example. While on vacation at Disneyland Paris, you start wondering about the mean age of French people. To get an answer, you ask ten people stood nearby about their ages. Their mean age is 24.6 years old. Do you think this will be a good estimate of the mean age of all French citizens? On the left, you can see mean ages taken from the French census. Notice that the population has been gradually getting older as birth rates decrease and life expectancy increases. In 2015, the mean age was over forty, so our estimate of 24.6 is way off. The problem is that the family-friendly fun at Disneyland means that the sample ages weren't representative of the general population. There are generally more eight-year-olds than eighty-year-olds riding rollercoasters.
## Convenience sampling coffee ratings
Let's return to the coffee ratings dataset and look at the mean cup points population parameter. The mean is about 82. One form of convenience sampling would be to take the first ten rows, rather than the random rows we saw in the previous video. We can take the first 10 rows with the pandas head method. The mean cup points from this sample is higher at 89. 
```Python
coffee_ratings["total_cup_points"].mean()
>>82.15120328849028

coffee_ratings_first10 = coffee_ratings.head(10)
coffee_ratings_first10["total_cup_points"].mean()
>>89.1
```
The discrepancy suggests that coffees with higher cup points appear near the start of the dataset. Again, the convenience sample isn't representative of the whole population.
## Visualising selection bias
Histograms are a great way to visualise the selection bias. We can create a histogram of the total cup points from the population, which contains values ranging from around 59 to around 91. The `np.arange()` function can be used to create bins of width 2 from 59 to 91. Recall that the stop value in np.arange() is exclusive, so we specify 93, not 91. Here's the same code to generate a histogram for the convenience sample.
```Python
import matplotlib.pyplot as plt
import numpy as np
coffee_ratings["total_cup_points"].hist(bins=np.arange(59, 93, 2))
plt.show()

coffee_ratings_first10["total_cup_points"].hist( \ 
						bins=np.arange(59, 93, 2))
plt.show()
```
Comparing the two histograms, it is clear that the distribution of the sample is not the same as the population: all of the sample values are on the right-hand side of the plot. This time, we'll compare the total_cup_points distribution of the population with a random sample of 10 coffees.
```Python
coffee_sample = coffee_ratings.sample(n=10)
coffee_sample["total_cup_points"].hist(bins=np.arange(59, 93, 2))
plt.show()
```
Notice how the shape of the distributions is more closely aligned when random sampling is used.
## Let's practice!
Let's plot some histograms!