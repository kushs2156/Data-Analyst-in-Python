In this lesson, we'll discuss a few other probability distributions.
## Exponential distribution
The first distribution is the exponential distribution, which represents the probability of a certain time passing between Poisson events. We can use the exponential distribution to predict, for example, the probability of more than 1 day between adoptions, the probability of fewer than 10 minutes between restaurant arrivals, and the probability of 6-8 months passing between earthquakes. Just like the Poisson distribution, the time unit doesn't matter as long as it's consistent. The exponential distribution uses the same lambda value, which represents the rate, that the Poisson distribution does. Note that lambda and rate mean the same value in this context. It's also continuous, unlike the Poisson distribution, since it represents time.
![[Pasted image 20250220173833.png]]

For example, let's say that one customer service ticket is created every 2 minutes. We can rephrase this so it's in terms of a time interval of one minute, so half of a ticket is created each minute. We'll use 0.5 as the lambda value. The rate affects the shape of the distribution and how steeply it declines.

Recall that lambda is the expected value of the Poisson distribution, which measures frequency in terms of rate or number of events. In our customer service ticket example, this means that the expected number of requests per minute is 0.5. The exponential distribution measures frequency in terms of time between events. The expected value of the exponential distribution can be calculated by taking 1 divided by lambda. 
$$
Expected \, value \, of \, exponential \, distribution = \frac{1}{\lambda}
$$
In our example, the expected time between requests is 1 over 0.5, which is 2, so there is an average of 2 minutes between requests.
## How long until a new request is created?
Similar to other continuous distributions, we can use `expon.cdf` to calculate probabilities. The probability of waiting less than 1 minute for a new request is calculated using expon.cdf, passing in 1 followed by a 2, which gives us about an 40% chance. 
```Python
from scipy.stats import expon
expon.cdf(1, scale=2)
>>0.3934693402873666

1 - expon.cdf(4, scale=2)
>>0.1353352832366127

expon.cdf(4, scale=2) - expon.cdf(1, scale=2)
>>0.4711953764760207
```
Note that we're passing in 2, not the lambda value which is 0.5. The probability of waiting more than 4 minutes can be found using `1 - expon.cdf` of 4, 2, giving a 13% chance. Finally, the probability of waiting between 1 and 4 minutes can be found by taking expon.cdf of 4 and subtracting expon.cdf of 1. There's a 50% chance you'll wait between 1 and 4 minutes.
## (Student's) t-distribution
The next distribution is the t-distribution, which is also sometimes called Student's t-distribution. Its shape is similar to the normal distribution, but not quite the same. If we compare the normal distribution, in blue, with the t-distribution with one degree of freedom, in orange, the t-distribution's tails are thicker. This means that in a t-distribution, observations are more likely to fall further from the mean.
![[Pasted image 20250220173248.png]]
The t-distribution has a parameter called degrees of freedom, which affects the thickness of the distribution's tails. Lower degrees of freedom results in thicker tails and a higher standard deviation. As the number of degrees of freedom increases, the distribution looks more and more like the normal distribution.
## Log-normal distribution
The last distribution we'll discuss is the log-normal distribution. Variables that follow a log-normal distribution have a logarithm that is normally distributed. This results in distributions that are skewed, unlike the normal distribution. There are lots of real-world examples that follow this distribution, such as the length of chess games, blood pressure in adults, and the number of hospitalisations in the 2003 SARS outbreak.
![[Pasted image 20250220173622.png]]
## Let's practice!
In addition to the three in this video, there are lots of other probability distributions that are out of the scope of this course, but that you can learn about in other DataCamp courses. For now, it's time to practice the distributions you've learned so far!