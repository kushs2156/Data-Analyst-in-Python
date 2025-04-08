We can use discrete distributions to model situations that involve discrete or countable variables, but how can we model continuous variables?

Let's start with an example. The city bus arrives once every twelve minutes, so if you show up at a random time, you could wait anywhere from 0 minutes if you just arrive as the bus pulls in, up to 12 minutes if you arrive just as the bus leaves. Let's model this scenario with a probability distribution. There are an infinite number of minutes we could wait since we could wait 1 minute, 1.5 minutes, 1.53 minutes, and so on, so we can't create individual blocks like we could with a discrete variable. Instead, we'll use a continuous line to represent probability. The line is flat since there's the same probability of waiting any time from 0 to 12 minutes. This is called the continuous uniform distribution.

Now that we have our distribution, let's figure out what the probability is that we'll wait between 4 and 7 minutes. Just like with discrete distributions, we can take the area from 4 to 7 to calculate probability. The width of this rectangle is 7 minus 4 which is 3. The height is one twelfth. Multiplying those together to get area, we get 3/12 or 25%.
## Uniform distribution in Python
Let's use the uniform distribution in Python to calculate the probability of waiting 7 minutes or less. We need to import `uniform` from `scipy.stats`. We can call `uniform.cdf` and pass it 7, followed by the lower and upper limits, which in our case is 0 and 12. The probability of waiting less than 7 minutes is about 58%.
```Python
from scipy.stats import uniform
uniform.cdf(7, 0, 12)
>>0.5833333

1 - uniform.cdf(7, 0, 12)
>>0.4166667
```
If we want the probability of waiting more than 7 minutes, we need to take 1 minus the probability of waiting less than 7 minutes.

How do we calculate the probability of waiting 4 to 7 minutes using Python? 
We can start with the probability of waiting less than 7 minutes, then subtract the probability of waiting less than 4 minutes. This gives us 25%.
```Python
uniform.cdf(7, 0, 12) - uniform.cdf(4, 0, 12)
>>0.25
```
To calculate the probability of waiting between 0 and 12 minutes, we multiply 12 by 1/12, which is 1, or 100%. This makes sense since we're certain we'll wait anywhere from 0 to 12 minutes.
## Generating random numbers according to uniform distribution
To generate random numbers according to the uniform distribution, we can use `uniform.rvs`, which takes in the minimum value, maximum value, followed by the number of random values we want to generate. Here, we generate 10 random values between 0 and 5.
```Python
uniform.rvs(0, 5, size=10)
```
## Other continuous distributions
Continuous distributions can take forms other than uniform where some values have a higher probability than others. No matter the shape of the distribution, the area beneath it must always equal 1. This will also be true of other distributions you'll learn about later on in the course, like the normal distribution or exponential distribution, which can be used to model many real-life situations.
## Let's practice!
Time to practice working with continuous distributions.