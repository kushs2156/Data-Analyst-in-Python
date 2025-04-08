In this lesson, we'll begin to discuss summary statistics, some of which you may already be familiar with, like mean and median. In this video, we'll look at data about different mammals' sleep habits.

Before we dive in, let's remind ourselves how histograms work. A histogram takes a bunch of data points and separates them into bins, or ranges of values. Here, there's a bin for 0 to 2 hours, 2 to 4 hours, and so on. The heights of the bars represent the number of data points that fall into that bin, so there's one mammal in the dataset that sleeps between 0 to 2 hours, and nine mammals that sleep two to four hours. Histograms are a great way to visually summarise the data, but we can use numerical summary statistics to summarise even further.

One way we could summarise the data is by answering the question, How long do mammals in this dataset typically sleep? To answer this, we need to figure out what the "typical" or "centre" value of the data is. We'll discuss three different definitions, or measures, of centre: mean, median, and mode.
## Measures of centre: mean
The mean, often called the average, is one of the most common ways of summarising data. To calculate mean, we add up all the numbers of interest and divide by the total number of data points, which is 83 here. This gives us 10.43 hours of sleep. In Python, we can use NumPy's mean function, passing it the variable of interest.
```Python
import numpy as np
np.mean(msleep['sleep_total'])
>>10.43373
```
## Measures of centre: median
Another measure of centre is the median. The median is the value where 50% of the data is lower than it, and 50% of the data is higher. We can calculate this by sorting all the data points and taking the middle one, which would be index 41 in this case. This gives us a median of 10.1 hours of sleep. In Python, we can use `np.median` to do the calculations for us.
```Python
msleep['sleep_total'].sort_values().iloc[41]
>>10.1

np.median(msleep['sleep_total'])
>>10.1
```
## Measures of centre: mode
The mode is the most frequent value in the data. If we count how many occurrences there are of each sleep_total and sort in descending order, there are 4 mammals that sleep for 12.5 hours, so this is the mode. The mode of the vore variable, which indicates the animal's diet, is herbivore. We can also find the mode using the mode function from the statistics module. 
```Python
msleep['sleep_total'].value_counts()

import statistics
statistics.mode(msleep['vore'])
>>'herbi'
```
Mode is often used for categorical variables, since categorical variables can be unordered and often don't have an inherent numerical representation.
## Adding an outlier
Now that we have lots of ways to measure centre, how do we know which one to use? Let's look at an example. Here, we have all of the insectivores in the dataset.
```Python
# Subset msleep to select rows where 'vore' equals 'insecti'
msleep[msleep['vore'] == 'insecti']

msleep[msleep['vore'] == 'insecti']['sleep_total'].agg([np.mean, 
														np.median])
>>mean    16.53
>>median  18.9
>>Name: sleep_total, dtype: float64
```
We get a mean sleep time of 16.5 hours and a median sleep time of 18.9 hours. Now let's say we've discovered a new mystery insectivore that never sleeps. If we take the mean and median again, we get different results. The mean went down by more than 3 hours, while the median changed by less than an hour. This is because the mean is much more sensitive to extreme values than the median. Since the mean is more sensitive to extreme values, it works better for symmetrical data like this. Notice that the mean, in black, and median, in red, are quite close.

However, if the data is skewed, meaning it's not symmetrical, like this, median is usually better to use. In this histogram, the data is piled up on the right, with a tail on the left. Data that looks like this is called left-skewed data. When data is piled up on the left with a tail on the right, it's right-skewed. When data is skewed, the mean and median are different. The mean is pulled in the direction of the skew, so it's lower than the median on the left-skewed data, and higher than the median on the right-skewed data. Because the mean is pulled around by the extreme values, it's better to use the median since it's less affected by outliers.
## Let's practice!
Let's practice using measures of centre.