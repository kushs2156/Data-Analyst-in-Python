Welcome to Chapter 3! In this chapter, we'll focus on visualisations that involve categorical variables. The first two plots we'll look at are count plots and bar plots.
## Categorical plots
Count plots and bar plots are two types of visualisations that Seaborn calls "categorical plots". Categorical plots involve a categorical variable, which is a variable that consists of a fixed, typically small number of possible values, or categories. These types of plots are commonly used when we want to make comparisons between different groups. We began to explore categorical plots in Chapter 1 with count plots. As a reminder, a count plot displays the number of observations in each category. We saw several examples of count plots in earlier chapters, like the number of men reporting that they feel masculine. Most men surveyed here feel "somewhat" or "very" masculine.
## `catplot()`
Just like we used "relplot()" to create different types of relational plots, in this chapter we'll be using "catplot()" to create different types of categorical plots. "catplot()" offers the same flexibility that "relplot()" does, which means it will be easy to create subplots if we need to using the same "col" and "row" parameters.

To see how "catplot()" works, let's return to the masculinity count plot. Below, we see how we originally created a count plot with the "countplot()" function.
```Python
import matplotlib.pyplot as plt
import seaborn as sns

sns.countplot(x="how_masculine", data=masculinity_data)
plt.show()
```
To make this plot with "catplot()" instead, we change the function name to "catplot()" and use the "kind" parameter to specify what kind of categorical plot to use. In this case, we'll set kind equal to the word "count".
```Python
sns.catplot(x="how_masculine", data=masculinity_data,
			kind="count")
plt.show()
```

Sometimes there is a specific ordering of categories that makes sense for these plots. In this case, it makes more sense for the categories to be in order from not masculine to very masculine. To change the order of the categories, create a list of category values in the order that you want them to appear, and then use the "order" parameter. This works for all types of categorical plots, not just count plots.
```Python
category_order = ["No answer", "Not at all", "Not very",
				  "Somewhat", "Very"]
sns.catplot(x="how_masculine", data=masculinity_data,
			kind="count", order=category_order)
plt.show()
```
## Bar plots
Bar plots look similar to count plots, but instead of the count of observations in each category, they show the mean of a quantitative variable among observations in each category. This bar plot uses the tips dataset and shows the average bill paid among people who visited the restaurant on each day of the week. From this, we can see that the average bill is slightly higher on the weekends. To create this bar plot, we use "catplot". Specify the categorical variable "day" on the x-axis, the quantitative variable "total bill" on the y-axis, and set the "kind" parameter equal to "bar".
```Python
import matplotlib.pyplot as plt
import seaborn as sns

sns.catplot(x="day", y="total_bill", data=tips, kind="bar")
plt.show()
```
## Confidence intervals
Notice also that Seaborn automatically shows 95% confidence intervals for these means. Just like with line plots, these confidence intervals show us the level of uncertainty we have about these estimates. Assuming our data is a random sample of some population, we can be 95% sure that the true population mean in each group lies within the confidence interval shown. If we want to turn off these confidence intervals, we can do this by setting the "ci" parameter equal to None - just like we did with line plots.
## Changing the orientation
Finally, you can also change the orientation of the bars in bar plots and count plots by switching the x and y parameters. However, it is fairly common practice to put the categorical variable on the x-axis.
```Python
sns.catplot(x="total_bill", y="day", data=tips, kind="bar")
plt.show()
```
## Let's practice!
We'll introduce more types of categorical plots later in the chapter, but for now, let's practice what we've learned!