Welcome! So far we've seen several types of categorical plots including count plots, bar plots, and box plots. In this lesson, we'll see one final categorical plot: point plots.
## What are point plots?
Point plots show the mean of a quantitative variable for the observations in each category, plotted as a single point. This point plot uses the tips dataset and shows the average bill among smokers versus non-smokers. The vertical bars extending above and below the mean represent the 95% confidence intervals for that mean. Just like the confidence intervals we saw in line plots and bar plots, these confidence intervals show us the level of uncertainty we have about these mean estimates. Assuming our data is a random sample of some population, we can be 95% sure that the true population mean in each group lies within the confidence interval shown.
## Point plots vs. line plots
You may be thinking: point plots look a lot like line plots. What's the difference? Both line plots and point plots show the mean of a quantitative variable and 95% confidence intervals for the mean. However, there is a key difference. Line plots are relational plots, so both the x- and y-axis are quantitative variables. In a point plot, one axis - usually the x-axis - is a categorical variable, making it a categorical plot.
## Point plots vs. bar plots
You may also be thinking: point plots seem to show the same information as bar plots. For each category, both show the mean of a quantitative variable and the confidence intervals for those means. When should we use one over the other? Let's look at an example using data from the masculinity survey that we've seen in prior lessons. This is a bar plot of the percent of men per age group surveyed who report thinking that it's important that others see them as masculine, with subgroups based on whether they report feeling masculine or not. This is the same information, represented as a point plot. In the point plot, it's easier to compare the heights of the subgroup points when they're stacked above each other. In the point plot, it's also easier to look at the differences in slope between the categories than it is to compare the heights of the bars between them.
## Creating a point plot
Here's the code to create the point plot we just saw. Since this is a categorical plot, we use "catplot" and set "kind" equal to "point".
```Python
import matplotlib.pyplot as plt
import seaborn as sns

sns.catplot(x="age", y="masculinity_important",
			data=masculinity_data, hue="feel_masculine",
			kind="point")
plt.show()
```
Sometimes we may want to remove the lines connecting each point, perhaps because we only wish to compare within a category group and not between them. To do this, set the "join" parameter equal to False.
```Python
sns.catplot(x="age", y="masculinity_important",
			data=masculinity_data, hue="feel_masculine",
			kind="point", join=False)
plt.show()
```
## Displaying the median
Let's return to the point plot using the tips dataset and go over a few more ways to customise your point plots. Here is the point plot of average bill comparing smokers to non-smokers.
```Python
sns.catplot(x="smoker", y="total_bill", data=tips, kind="point")
plt.show()
```
To have the points and confidence intervals be calculated for the median instead of the mean, import the median function from the NumPy library and set "estimator" equal to the NumPy median function. Why might you want to use the median instead of the mean? The median is more robust to outliers, so if your dataset has a lot of outliers, the median may be a better statistic to use.
```Python
from numpy import median

sns.catplot(x="smoker", y="total_bill", data=tips, 
			kind="point", estimator=median)
plt.show()
```
## Customising the confidence intervals
You can also customise the way that the confidence intervals are displayed. To add “caps” to the end of the confidence intervals, set the “capsize” parameter equal to the desired width of the caps. In this case, we chose a width of 0.2.
```Python
sns.catplot(x="smoker", y="total_bill", data=tips, 
			kind="point", capsize=0.2)
plt.show()
```
## Turning off confidence intervals
Finally, like we saw with line plots and bar plots, you can turn the confidence intervals off by setting the "ci" parameter equal to None.
## Let's practice!
Alright! Now that we've covered how to interpret and customise point plots, let's practice what we've learned!