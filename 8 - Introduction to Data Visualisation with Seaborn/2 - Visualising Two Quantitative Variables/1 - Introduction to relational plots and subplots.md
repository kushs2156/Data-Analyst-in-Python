Many questions in data science are centered around describing the relationship between two quantitative variables. Seaborn calls plots that visualise this relationship "relational plots".
## Questions about quantitative variables
So far we've seen several examples of questions about the relationship between two quantitative variables, and we answered them with scatter plots. These examples include: "do taller people tend to weigh more?", "what's the relationship between the number of absences a student has and their final grade?" and "how does a country's GDP relate to the percent of the population that can read and write?" Because they look at the relationship between two quantitative variables, these scatter plots are all considered relational plots.
## Visualising subgroups
While looking at a relationship between two variables at a high level is often informative, sometimes we suspect that the relationship may be different within certain subgroups. In the last chapter, we started to look at subgroups by using the "hue" parameter to visualise each subgroup using a different colour on the same plot. In this lesson, we'll try out a different method: creating a separate plot per subgroup.
## Introducing `relplot()`
To do this, we're going to introduce a new Seaborn function: `relplot()`. `relplot()` stands for "relational plot" and enables you to visualise the relationship between two quantitative variables using either scatter plots or line plots. You've already seen scatter plots, and you'll learn about line plots later in this chapter. Using relplot() gives us a big advantage: the ability to create subplots in a single figure. Because of this advantage, we'll be using relplot() instead of scatterplot() for the rest of the course.
## `scatterplot()` vs. `relplot()`
Let's return to our scatter plot of total bill versus tip amount from the tips dataset. Below, we see how to create a scatter plot with the "scatterplot" function. To make it with "relplot()" instead, we change the function name to "relplot()" and use the "kind" parameter to specify what kind of relational plot to use - scatter plot or line plot. In this case, we'll set kind equal to the word "scatter".
```Python
import matplotlib.pyplot as plt
import seaborn as sns

sns.scatterplot(x="total_bill", y="tip", data=tips)
plt.show()

sns.relplot(x="total_bill", y="tip", data=tips, kind="scatter"
			col="smoker")
plt.show()

sns.relplot(x="total_bill", y="tip", data=tips, kind="scatter"
			row="smoker")
plt.show()
```
By setting "col" equal to "smoker", we get a separate scatter plot for smokers and non-smokers, arranged horizontally in columns. If you want to arrange these vertically in rows instead, you can use the "row" parameter instead of "col".

It is possible to use both "col" and "row" at the same time. Here, we set "col" equal to smoking status and "row" equal to the time of day (lunch or dinner). Now we have a subplot for each combination of these two categorical variables.
```Python
import matplotlib.pyplot as plt
import seaborn as sns

sns.relplot(x="total_bill", y="tip", data=tips, kind="scatter"
			row="time", col="smoker")
plt.show()
```
## Subgroups for days of the week
As another example, let's look at subgroups based on day of the week. There are four subplots here, which can be a lot to show in a single row. To address this, you can use the "col_wrap" parameter to specify how many subplots you want per row. Here, we set "col_wrap" equal to two plots per row.
```Python
import matplotlib.pyplot as plt
import seaborn as sns

sns.relplot(x="total_bill", y="tip", data=tips, kind="scatter",
			col="day", col_wrap=2)
plt.show()
```
We can also change the order of the subplots by using the "col_order" and "row_order" parameters and giving it a list of ordered values.
```Python
import matplotlib.pyplot as plt
import seaborn as sns

sns.relplot(x="total_bill", y="tip", data=tips, kind="scatter",
			col="day", col_wrap=2,
			col_order=["Thur", "Fri", "Sat", "Sun"])
plt.show()
```
## Let's practice!
Alright! Now it's time to practice what we've learned and create some relational plots!