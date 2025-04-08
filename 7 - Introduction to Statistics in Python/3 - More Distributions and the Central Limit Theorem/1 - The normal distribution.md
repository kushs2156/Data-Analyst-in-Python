The next probability distribution we'll discuss is the normal distribution. It's one of the most important probability distributions you'll learn about since a countless number of statistical methods rely on it, and it applies to more real-world situations than the distributions we've covered so far.
## What is a normal distribution?
The normal distribution looks like this. Its shape is commonly referred to as a "bell curve". The normal distribution has a few important properties. First, it's symmetrical, so the left side is a mirror image of the right. Second, just like any continuous distribution, the area beneath the curve is 1. Third, the probability never hits 0, even if it looks like it does at the tail ends. Only 0.006% of its area is contained beyond the edges of this graph.
![[Standard_deviation_diagram.webp]]
The normal distribution is described by its mean and standard deviation. Here is a normal distribution with a mean of 20 and standard deviation of 3, and here is a normal distribution with a mean of 0 and a standard deviation of 1. When a normal distribution has mean 0 and a standard deviation of 1, it's a special distribution called the standard normal distribution Notice how both distributions have the same shape, but their axes have different scales.
## Areas under the normal distribution
For the normal distribution, 68% of the area is within 1 standard deviation of the mean. 95% of the area falls within 2 standard deviations of the mean, and 99.7% of the area falls within three standard deviations. This is sometimes called the 68-95-99.7 rule.
## Approximating data with the normal distribution
There's lots of real-world data shaped like the normal distribution. For example, here is a histogram of the heights of women that participated in the National Health and Nutrition Examination Survey. The mean height is around 161cm and the standard deviation is about 7cm. Since this height data closely resembles the normal distribution, we can take the area under a normal distribution with mean 161 and standard deviation 7 to approximate what percent of women fall into different height ranges.

For example, what percent of women are shorter than 154cm? We can answer this using `norm.cdf` from scipy.stats, which takes the area of the normal distribution less than some number. We pass in the number of interest, 154, followed by the mean and standard deviation of the normal distribution we're using. This gives us about 16% of women are shorter than 154cm.
```Python
from scipy.stats import norm
norm.cdf(154, 161, 7)
>>0.158655

1 - norm.cdf(154, 161, 7)
>>0.841345
```
To find the percent of women taller than 154cm, we can take 1 minus the area on the left of 154, which equals the area to the right of 154.

To get the percent of women between 154 and 157cm tall we can take the area below 157 and subtract the area below 154, which leaves us the area between 154 and 157.
```Python
norm.cdf(157, 161, 7) - norm.cdf(154, 161, 7)
>>0.1252
```

We can also calculate percentages from heights using `norm.ppf`. To figure out what height 90% of women are shorter than, we pass 0.9 into norm.ppf along with the same mean and standard deviation we've been working with. This tells us that 90% of women are shorter than 170cm tall.
```Python
norm.ppf(0.9, 161, 7)
>>169.97086
```

We can figure out the height 90% of women are taller than, since this is also the height that 10% of women are shorter than. We can take 1 minus 0.9 to get 0.1, which we'll use as the first argument of norm.ppf.
```Python
norm.ppf(0.1, 161, 7)
>>152.029
```
## Generating random numbers
Just like with other distributions, we can generate random numbers from a normal distribution using `norm.rvs`, passing in the distribution's mean and standard deviation, as well as the sample size we want. Here, we've generated 10 more random heights.
```Python
# Generate 10 random heights
norm.rvs(161, 7, size=10)
```
## Let's practice!
Your turn to practice using the normal distribution!