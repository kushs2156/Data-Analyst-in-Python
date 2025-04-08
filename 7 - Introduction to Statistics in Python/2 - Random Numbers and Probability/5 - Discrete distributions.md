In this lesson, we'll take a deeper dive into probability and begin looking at probability distributions.
## Rolling the dice
Let's consider rolling a standard, six-sided die. There are six numbers, or six possible outcomes, and every number has one sixth, or about a 17% chance of being rolled. This is an example of a probability distribution. This is similar to the scenario from earlier, except we had names instead of numbers. Just like rolling a die, each outcome, or name, had an equal chance of being chosen.
## Probability distribution
A probability distribution describes the probability of each possible outcome in a scenario. We can also talk about the expected value of a distribution, which is the mean of a distribution. We can calculate this by multiplying each value by its probability (one sixth in this case) and summing, so the expected value of rolling a fair die is 3.5.
$$
(1 \times \frac{1}{6}) + (2 \times \frac{1}{6}) + (3 \times \frac{1}{6}) + (4 \times \frac{1}{6}) + (5 \times \frac{1}{6}) + (6 \times \frac{1}{6}) = 3.5
$$
We can visualise this using a bar plot, where each bar represents an outcome, and each bar's height represents the probability of that outcome. We can calculate probabilities of different outcomes by taking areas of the probability distribution. For example, what's the probability that our die roll is less than or equal to 2? To figure this out, we'll take the area of each bar representing an outcome of 2 or less. Each bar has a width of 1 and a height of one sixth, so the area of each bar is one sixth. We'll sum the areas for 1 and 2, to get a total probability of one third.
## Uneven die
Now let's say we have a die where the two got turned into a three. This means that we now have a 0% chance of getting a 2, and a 33% chance of getting a 3. To calculate the expected value of this die, we now multiply 2 by 0, since it's impossible to get a 2, and 3 by its new probability, one third. This gives us an expected value that's slightly higher than the fair die.
$$
(1 \times \frac{1}{6}) + (2 \times 0) + (3 \times \frac{1}{3}) + (4 \times \frac{1}{6}) + (5 \times \frac{1}{6}) + (6 \times \frac{1}{6}) = 3.67
$$
When we visualise these new probabilities, the bars are no longer even. With this die, what's the probability of getting something less than or equal to 2? There's a one sixth probability of getting 1, and zero probability of getting 2, which sums to one sixth.
## Discrete probability distributions
The probability distributions you've seen so far are both discrete probability distributions, since they represent situations with discrete outcomes. Recall from chapter 1 that discrete variables can be thought of as counted variables. In the case of a die, we're counting dots, so we can't roll a 1.5 or 4.3. When all outcomes have the same probability, like a fair die, this is a special distribution called a **discrete uniform distribution**.
## Sampling from discrete distributions
Just like we sampled names from a box, we can do the same thing with probability distributions like the ones we've seen. Here's a DataFrame called die that represents a fair die, and its expected value is 3.5. We'll sample from it 10 times to simulate 10 rolls. Notice that we sample with replacement so that we're sampling from the same distribution every time.
```Python
np.mean(die['number'])
>>3.5

rolls_10 = die.sample(10, replace = True)

rolls_10['number'].hist(bins=np.linspace(1,7,7))
```
We can visualise the outcomes of the ten rolls using a histogram, defining the bins we want using `np.linspace`. Notice that we have different numbers of 1's, 2's, 3's, and so on since the sample was random, even though on each roll we had the same probability of rolling each number. The mean of our sample is 3.0, which isn't super close to the 3.5 we were expecting. If we roll the die 100 times, the distribution of the rolls looks a bit more even, and the mean is closer to 3.5. If we roll 1000 times, it looks even more like the theoretical probability distribution and the mean closely matches 3.5.

This is called the ==law of large numbers==, which is the idea that as the size of your sample increases, the sample mean will approach the theoretical mean.
## Let's practice!
Time to solidify your knowledge of probability distributions.