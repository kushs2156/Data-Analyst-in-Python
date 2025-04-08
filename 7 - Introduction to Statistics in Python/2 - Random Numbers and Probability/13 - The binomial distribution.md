It's time to further expand your toolbox of distributions. In this video, you'll learn about the binomial distribution.

We'll start by flipping a coin, which has two possible outcomes, heads or tails, each with a probability of 50%. This is just one example of a binary outcome, or an outcome with two possible values. We could also represent these outcomes as a 1 and a 0, a success or a failure, and a win or a loss.
## A single flip
In Python, we can simulate this by importing `binom` from `scipy.stats` and using the `binom.rvs` function, which takes in the number of coins we want to flip, the probability of heads or success, and an argument called size, which is number of trials. size is a named argument, so we'll need to explicitly specify that the third argument corresponds to size, or we'll get incorrect results. This call will return a 1, which we'll count as a head, or a 0, which we'll count as tails. We can use binom.rvs 1, 0.5, size equals 1 to flip 1 coin, with a 50% probability of heads, 1 time.
```Python
from scipy.stats import binom
binom.rvs(1, 0.5, size=1)
>>array([1])
```
## One flip many times
To perform eight coin flips, we can change the size argument to 8, which will flip 1 coin with a 50% chance of heads 8 times. This gives us a set of 8 ones and zeros.
```Python
binom.rvs(1, 0.5, size=8)
>>array([0, 1, 1, 0, 1, 0, 1, 1])
```
## Many flips one time
If we swap the first and last arguments, we flip eight coins one time. This gives us one number, which is the total number of heads or successes.
```Python
binom.rvs(8, 0.5, size=1)
>>array([5])
```
Similarly, we can pass 3 as the first argument, and set size equal to 10 to flip 3 coins. This returns 10 numbers, each representing the total number of heads from each set of flips.
```Python
binom.rvs(3, 0.5, size=10)
>>array([0, 3, 2, 1, 3, 0, 2, 2, 0, 0])
```
## Other probabilities
We could also have a coin that's heavier on one side than the other, so the probability of getting heads is only 25%. To simulate flips with this coin, we'll adjust the second argument of binom.rvs to 0.25. The result has lower numbers, since getting multiple heads isn't as likely with the new coin.
```Python
binom.rvs(3, 0.25, size=10)
>>array([1, 1, 1, 1, 0, 0, 2, 0, 1, 0])
```
## Binomial distribution
The binomial distribution describes the probability of the number of successes in a sequence of independent trials. In other words, it can tell us the probability of getting some number of heads in a sequence of coin flips. Note that this is a discrete distribution since we're working with a countable outcome. The binomial distribution can be described using two parameters, n and p. **n** represents the total number of trials being performed, and **p** is the probability of success. n and p are also the third and second arguments of binom.rvs. Here's what the distribution looks like for 10 coins. We have the biggest chance of getting 5 heads total, and a much smaller chance of getting 0 heads or 10 heads.

To get the probability of getting 7 heads out of 10 coins, we can use `binom.pmf`. The first argument is the number of heads or successes. The second argument is the number of trials, n, and the third is the probability of success, p. If we flip 10 coins, there's about a 12% chance that exactly 7 of them will be heads.
```Python
# binom.pmf(num heads, num trials, prob of heads)
binom.pmf(7, 10, 0.5)
>>0.1171875
```
`binom.cdf` gives the probability of getting a number of successes less than or equal to the first argument. The probability of getting 7 or fewer heads out of 10 coins is about 95%.
```Python
binom.cdf(7, 10, 0.5)
>>0.9453125

1 - binom.cdf(7, 10, 0.5)
>>0.0546875
```
We can take 1 minus the probability of getting 7 or fewer heads to get the probability of a number of successes greater than the first argument.

The expected value of the binomial distribution can be calculated by multiplying n times p. The expected number of heads we'll get from flipping 10 coins is 10 times 0.5, which is 5.
## Independence
It's important to remember that in order for the binomial distribution to apply, each trial must be independent, so the outcome of one trial shouldn't have an effect on the next. For example, if we're picking randomly from these cards with zeros and ones, we have a 50-50 chance of getting a 0 or a 1. But since we're sampling without replacement, the probabilities for the second trial are different due to the outcome of the first trial. Since these trials aren't independent, we can't calculate accurate probabilities for this situation using the binomial distribution.
## Let's practice!
Time to explore binary outcomes using the binomial distribution.