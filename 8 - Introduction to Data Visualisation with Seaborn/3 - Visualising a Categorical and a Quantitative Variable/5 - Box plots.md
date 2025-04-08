Hello! In this video we'll learn how to create a new type of categorical plot: the box plot.
## What is a box plot?
A box plot shows the distribution of quantitative data. The coloured box represents the 25th to 75th percentile, and the line in the middle of the box represents the median. The whiskers give a sense of the spread of the distribution, and the floating points represent outliers. Box plots are commonly used as a way to compare the distribution of a quantitative variable across different groups of a categorical variable. To see this, let's look at this example. The box plot shown here uses the tips dataset and compares the distribution of the total bill paid per table across the different days of the week. From this box plot we can quickly see that the median bill is higher on Saturday and Sunday, but the spread of the distribution is also larger. This comparison would be much harder to do with other types of visualisations.
## How to create a box plot
Now let's look at how to create a box plot in Seaborn. While Seaborn does have a "boxplot()" function, we'll be using the "catplot()" function that we introduced in an earlier lesson because it makes it easy to create subplots using the "col" and "row" parameters. We'll put the categorical variable "time" on the x-axis and the quantitative variable "total bill" on the y-axis. Here, we want box plots, so we'll specify kind="box". That's it! We have a nice looking box plot. Next, we'll look at different ways to customise this plot.
```Python
import matplotlib.pyplot as plt
import seaborn as sns

g = sns.catplot(x="time", y="total_bill", data=tips,
				kind="box")
plt.show()
```
## Change the order of categories
As a reminder, "catplot" allows you to change the order of the categories using the "order" parameter. Here, we specified that "dinner" should be shown before "lunch".
```Python
g = sns.catplot(x="time", y="total_bill", data=tips,
				kind="box",
				order=["Dinner", "Lunch"])
plt.show()
```
## Omitting the outliers using `sym`
Occasionally, you may want to omit the outliers from your box plot. You can do this using the "sym" parameter. If you pass an empty string into "sym", it will omit the outliers from your plot altogether. "Sym" can also be used to change the appearance of the outliers instead of omitting them.
```Python
g = sns.catplot(x="time", y="total_bill", data=tips,
				kind="box", sym="")
plt.show()
```
## Changing the whiskers using `whis`
By default, the whiskers extend to 1.5 times the interquartile range, or "IQR". The IQR is the 25th to the 75th percentile of a distribution of data. If you want to change the way the whiskers in your box plot are defined, you can do this using the "whis" parameter. There are several options for changing the whiskers. You can change the range of the whiskers from 1.5 times the IQR (which is the default) to 2 times the IQR by setting `whis=2.0`. Alternatively, you can have the whiskers define specific lower and upper percentiles by passing in a list of the lower and upper values. In this example, passing in `whis=[5,95]` will result in the lower whisker being drawn at the 5th percentile and the upper whisker being drawn at the 95th percentile. Finally, you may just want to draw the whiskers at the min and max values. You can do this by specifying the lower percentile as 0 and the upper percentile as 100, `whis=[0,100]`. Here's an example where the whiskers are set to the min and max values. Note that there are no outliers, because the box and whiskers cover the entire range of the data.
```Python
g = sns.catplot(x="time", y="total_bill", data=tips,
				kind="box", whis=[0, 100])
plt.show()
```
## Let's practice!
Let's now practice creating and customising box plots!
