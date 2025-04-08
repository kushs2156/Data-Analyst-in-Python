Hi! Welcome to the course! I’m James, and I’ll be your host as we delve into the world of sampling data with Python. To start, let’s look at what sampling is and why it might be useful. Let's consider the problem of counting how many people live in France. The standard approach is to take a census. This means contacting every household and asking how many people live there. Since there are millions of people in France, this is a really expensive process. Even with modern data collection technology, most countries will only conduct a census every five or ten years due to the cost. In 1786, Pierre-Simon Laplace realised you could estimate the population with less effort. Rather than asking every household who lived there, he asked a small number of households and used statistics to estimate the number of people in the whole population. This technique of working with a subset of the whole population is called sampling.
## Population vs. sample
Two definitions are important for this course. The population is the complete set of data that we are interested in. The previous example involved the literal population of France, but in statistics, it doesn't have to refer to people. One thing to bear in mind is that there is usually no equivalent of the census, so typically, we won't know what the whole population is like - more on this in a moment. The sample is the subset of data that we are working with.
## Coffee rating dataset
Here's a dataset of professional ratings of coffees. Each row corresponds to one coffee, and there are 1338 rows in the dataset. The coffee is given a score from 0 to 100, which is stored in the `total_cup_points` column. Other columns contain contextual information like the variety and country of origin and scores between 0 and 10 for attributes of the coffee such as aroma and body. These scores are averaged across all the reviewers for that particular coffee. It doesn't contain every coffee in the world, so we don't know exactly what the population of coffees is. However, there are enough here that we can think of it as our population of interest.
## Points vs. flavour
Let's consider the relationship between cup points and flavour by selecting those two columns. This dataset contains all 1338 rows from the original dataset.
```Python
pts_vs_flavor_pop = coffee_ratings[["total_cup_points", "flavor"]]

pts_vs_flavor_samp = pts_vs_flavor_pop.sample(n=10)

cup_points_samp = coffee_ratings['total_cup_points'].sample(n=10)
```
The pandas `.sample()` method returns a random subset of rows. Setting `n=10` means ten random rows are returned. By default, rows from the original dataset can't appear in the sample dataset multiple times, so we are guaranteed to have ten unique rows in our sample. The .sample method also works on pandas Series. Here, using square-bracket subsetting retrieves the total_cup_points column as a Series, and the n argument specifies how many random values to return.
## Population parameters & point estimates
A **population parameter** is a **calculation** made on the **population dataset**. We aren't limited to counting values either; here, we calculate the mean of the cup points using NumPy. By contrast, a **point estimate**, or **sample statistic**, is a **calculation** based on the **sample dataset**. Here, the mean of the total cup points is calculated on the sample. Notice that the means are very similar but not identical.
```Python
import numpy as np

np.mean(pts_vs_flavor_pop['total_cup_points'])
>>82.15120328849028

np.mean(pts_vs_flavor_samp)
>>81.31800000000001
```
## Point estimates with pandas
Working with pandas can be easier than working with NumPy. These mean calculations can be performed using the `.mean()` pandas method.
```Python
pts_vs_flavor_pop['flavor'].mean()
>>7.526046337817639

pts_vs_flavor_samp['flavor'].mean()
>>7.485000000000001
```
## Let's practice!
Let's starting sampling!