Let's see how the size of the sample affects the accuracy of the point estimates we calculate. The sample size, calculated here with the len function, is the number of observations, that is, the number of rows in the sample. 
```Python
len(coffee_ratings.sample(n=300))
>>300

len(coffee_ratings.sample(frac=0.25))
>>334
```
That's true whichever method we use to create the sample. We'll stick to looking at simple random sampling since it works well in most cases and it's easier to reason about.
## Various sample sizes
Let's calculate a population parameter, the mean cup points of the coffees. It's around 82.15. This is our gold standard to compare against. 
```Python
coffee_ratings['total_cup_points'].mean()
>>82.15120328849028
```
If we take a sample size of ten, the point estimate of this parameter is wrong by about 0.88. Increasing the sample size to one hundred gets us closer; the estimate is only wrong by about 0.34. Increasing the sample size further to one thousand brings the estimate to about 0.03 away from the population parameter. 
```Python
coffee_ratings.sample(n=10)['total_cup_points'].mean()
>>83.027

coffee_ratings.sample(n=100)['total_cup_points'].mean()
>>82.4897

coffee_ratings.sample(n=1000)['total_cup_points'].mean()
>>82.1186
```
In general, larger sample sizes will give us more accurate results.
## Relative errors
For any of these sample sizes, we want to compare the population mean to the sample mean. This is the same code we just saw, but with the numerical sample size replaced with a variable named sample_size. The most common metric for assessing the difference between the population and a sample mean is the relative error. The relative error is the absolute difference between the two numbers; that is, we ignore any minus signs, divided by the population mean. Here, we also multiply by one hundred to make it a percentage.
$$
Relative \, error = 100 \times \frac{|population \, mean - sample \, mean|}{population \, mean}
$$
```Python
# Population parameter
population_mean = coffee_ratings['total_cup_points'].mean()

# Point estimate
sample_mean = coffee_ratings.sample(n=sample_size) \
	['total_cup_points'].mean()

# Relative error as a percentage
rel_error_pct = 100 * abs(population_mean-sample_mean) /
	population_mean
```
## Relative error vs. sample size
Here's a line plot of relative error versus sample size. 
```Python
import matplotlib.pyplot as plt
errors.plot(x="sample_size", y="relative_error", kind="line")
plt.show()
```
We see that the relative error decreases as the sample size increases, and beyond that, the plot has other important properties. Firstly, the blue line is really noisy, particularly for small sample sizes. If our sample size is small, the sample mean we calculate can be wildly different by adding one or two more random rows to the sample. Secondly, the amplitude of the line is quite steep, to begin with. When we have a small sample size, adding just a few more samples can give us much better accuracy. Further to the right of the plot, the line is less steep. If we already have a large sample size, adding a few more rows to the sample doesn't bring as much benefit. Finally, at the far right of the plot, where the sample size is the whole population, the relative error decreases to zero.
## Let's practice!
Let's explore sample sizes.