In this video, we'll talk about another probability distribution called the Poisson distribution.
## Poisson processes
Before we talk about probability, let's define a Poisson process. A Poisson process is a process where events appear to happen at a certain rate, but completely at random. For example, the number of animals adopted from an animal shelter each week is a Poisson process - we may know that on average there are 8 adoptions per week, but this number can differ randomly. Other examples would be the number of people arriving at a restaurant each hour, or the number of earthquakes per year in California. The time unit like, hours, weeks, or years, is irrelevant as long as it's consistent.
## Poisson distribution
The Poisson distribution describes the probability of some number of events happening over a fixed period of time. We can use the Poisson distribution to calculate the probability of at least 5 animals getting adopted in a week, the probability of 12 people arriving in a restaurant in an hour, or the probability of fewer than 20 earthquakes in California in a year.
## Lambda ($\lambda$)
The Poisson distribution is described by a value called lambda, which represents the average number of events per time period. In the animal shelter example, this would be the average number of adoptions per week, which is 8. This value is also the **expected value** of the distribution! The Poisson distribution with lambda equals 8 looks like this. Notice that it's a discrete distribution since we're counting events, and 7 and 8 are the most likely number of adoptions to happen in a week.

Lambda changes the shape of the distribution, so a Poisson distribution with lambda equals 1, in blue, looks quite different than a Poisson distribution with lambda equals 8, in green, but no matter what, the distribution's peak is always at its lambda value.
## Probability of a single value
Given that the average number of adoptions per week is 8, what's the probability of 5 adoptions in a week? Just like the other probability distributions, we can import `poisson` from `scipy.stats`. We'll use the `poisson.pmf` function, passing 5 as the first argument and 8 as the second argument to indicate the distribution's mean. 
```Python
from scipy.stats import poisson
poisson.pmf(5, 8)
>>0.09160366
```
This gives us about 9%.

To get the probability that 5 or fewer adoptions will happen in a week, use the `poisson.cdf` function, passing in the same numbers. This gives us about 20%.
```Python
poisson.cdf(5, 8)
>>0.1912361

1 - poisson.cdf(5, 8)
>>0.8087639
```
Just like other probability functions you've learned about so far, take 1 minus the "less than or equal to 5" probability to get the probability of more than 5 adoptions. There's an 81% chance that more than 5 adoptions will occur. If the average number of adoptions rises to 10 per week, there will be a 93% chance that more than 5 adoptions will occur.
## Sampling from a Poisson distribution
Just like other distributions, we can take samples from Poisson distributions using `poisson.rvs`. Here, we'll simulate 10 different weeks at the animal shelter. In one week, there are 14 adoptions, but only 6 in another.
```Python
poisson.rvs(8, size=10)
>>array([9, 9, 8, 7, 11, 3, 10, 6, 8, 14])
```
## The CLT still applies!
Just like other distributions, the sampling distribution of sample means of a Poisson distribution looks normal with a large number of samples.
## Let's practice!
Time to practice taking Poisson probabilities!