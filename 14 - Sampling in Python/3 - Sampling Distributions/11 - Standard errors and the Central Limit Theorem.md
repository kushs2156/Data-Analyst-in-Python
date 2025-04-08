The Gaussian distribution (also known as the normal distribution) plays an important role in statistics. Its distinctive bell-shaped curve has been cropping up throughout this course.
## Sampling distribution of mean cup points
Here are approximate sampling distributions of the mean cup points from the coffee dataset. Each histogram shows 5000 replicates, with different sample sizes in each case. Look at the x-axis labels. We already saw how increasing the sample size results in greater accuracy in our estimates of the population parameter, so the width of the distribution shrinks as the sample size increases. When the sample size is five, the x-axis ranges from 76 to 86, whereas, for a sample size of 320, the range is from 81.6 to 82.6. Now, look at the shape of each distribution. As the sample size increases, we can see that the shape of the curve gets closer and closer to being a normal distribution. At sample size five, the curve is only a very loose approximation since it isn't very symmetric. By sample size eighty, it is a very reasonable approximation.
## Consequences of the central limit theorem
What we just saw is, in essence, what the central limit theorem tells us. The means of independent samples have normal distributions. Then, as the sample size increases, we see two things. The distribution of these averages gets closer to being normal, and the width of this sampling distribution gets narrower.
## Population & sampling distribution means
Recall the population parameter of the mean cup points. We've seen this calculation before, and its value is 82.15. We can also calculate summary statistics on our sampling distributions to see how they compare. For each of our four sampling distributions, if we take the mean of our sample means, we can see that we get values that are pretty close to the population parameter that the sampling distributions are trying to estimate.

| Sample size | Mean sample mean    |
| ----------- | ------------------- |
| 5           | `82.18420719999999` |
| 20          | `82.1558634`        |
| 80          | `82.14510154999999` |
| 320         | `82.154017925`      |
## Population & sampling distribution standard deviations
Now let's consider the standard deviation of the population cup points. It's about 2.7. By comparison, if we take the standard deviation of the sample means from each of the sampling distributions using NumPy, we get much smaller numbers, and they decrease as the sample size increases. Note that when we are calculating a population standard deviation with pandas .std, we must specify ddof equals zero, as .std calculates a sample standard deviation by default. When we are calculating a standard deviation on a sample of the population using NumPy's std function, like in these calculations on the sampling distribution, we must specify a ddof of one. So what are these smaller standard deviation values?
- Specify `ddof=0` when calling `.std()` on populations
- Specify `ddof=1` when calling `np.std()` on samples or sampling distributions

| Sample size | Std dev sample mean   |
| ----------- | --------------------- |
| 5           | `1.1886358227738543`  |
| 20          | `0.5940321141669805`  |
| 80          | `0.2934024263916487`  |
| 320         | `0.13095083089190876` |

One other consequence of the central limit theorem is that if we divide the population standard deviation, in this case around 2.7, by the square root of the sample size, we get an estimate of the standard deviation of the sampling distribution for that sample size. It isn't exact because of the randomness involved in the sampling process, but it's pretty close.

| Sample size | Std dev sample mean   | Calculation                     | Result  |
| ----------- | --------------------- | ------------------------------- | ------- |
| 5           | `1.1886358227738543`  | `2.685858187306438 / sqrt(5)`   | `1.201` |
| 20          | `0.5940321141669805`  | `2.685858187306438 / sqrt(20)`  | `0.601` |
| 80          | `0.2934024263916487`  | `2.685858187306438 / sqrt(80)`  | `0.300` |
| 320         | `0.13095083089190876` | `2.685858187306438 / sqrt(320)` | `0.150` |
## Standard error
We just saw the impact of the sample size on the standard deviation of the sampling distribution. This standard deviation of the sampling distribution has a special name: the **standard error**. It is useful in a variety of contexts, from estimating population standard deviation to setting expectations on what level of variability we would expect from the sampling process.
## Let's practice!
Let's explore some sampling distributions.