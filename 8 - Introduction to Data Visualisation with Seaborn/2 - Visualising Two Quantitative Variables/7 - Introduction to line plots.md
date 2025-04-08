Hello! In this video we'll dive into a new type of relational plot: line plots.

In Seaborn, we have two types of relational plots: scatter plots and line plots. While each point in a scatter plot is assumed to be an independent observation, line plots are the visualisation of choice when we need to track the same thing over time. A common example is tracking the value of a company's stock over time, as shown here.
## Air pollution data
In this video, we'll be using data on the levels of air pollution in a city. There are many air collection stations around the city, each measuring the nitrogen dioxide level every hour for a single day. Long-term exposure to high levels of nitrogen dioxide can cause chronic lung diseases. Let's begin with the simple case where we have one data point per x-value. Here we have one row per hour over the course of the day with the average nitrogen dioxide level across all the stations in a column called "NO_2_mean".
## Scatter plot vs. line plot
This is a scatter plot with the average nitrogen dioxide level on the y-axis and the hour of the day on the x-axis. We're tracking the same thing over time, so a line plot would be a better choice.
```Python
import matplotlib.pyplot as plt
import seaborn as sns

sns.relplot(x="hour", y="NO_2_mean", data=air_df_mean,
			kind="scatter")
plt.show()
```
By specifying "kind" equals "line", we can create a line plot and more easily see how the average nitrogen dioxide level fluctuates throughout the day.
```Python
sns.relplot(x="hour", y="NO_2_mean", data=air_df_mean,
			kind="line")
plt.show()
```
## Subgroups by location
We can also track subgroups over time with line plots. Here we have the average nitrogen dioxide level for each region (North, South, East, and West) for each hour in the day. Setting the "style" and "hue" parameters equal to the variable name "location" creates different lines for each region that vary in both line style and colour. Here, we can see that the South region tends to have slightly higher average nitrogen dioxide levels compared to the other regions.
```Python
sns.relplot(x="hour", y="NO_2_mean", data=air_df_loc_mean,
			kind="line", style="location", hue="location",
			markers=True, dashes=False)
plt.show()
```
Setting the "markers" parameter equal to "True" will display a marker for each data point. The marker will vary based on the subgroup you've set using the "style" parameter. If you don't want the line styles to vary by subgroup, set the "dashes" parameter equal to "False".
## Multiple observations per x-value
Line plots can also be used when you have more than one observation per x-value. This dataset has a row for each station that is taking a measurement every hour. This is the scatter plot, displaying one point per observation. This is the line plot. If a line plot is given multiple observations per x-value, it will aggregate them into a single summary measure. By default, it will display the mean.
```Python
sns.relplot(x="hour", y="NO_2", data=air_df, kind="line")
plt.show()
```
Notice that Seaborn will automatically calculate a confidence interval for the mean, displayed by the shaded region. Assuming the air collection stations were randomly placed throughout the city, this dataset is a random sample of the nitrogen dioxide levels across the whole city. This confidence interval tells us that based on our sample, we can be 95% confident that the average nitrogen dioxide level for the whole city is within this range. Confidence intervals indicate the uncertainty we have about what the true mean is for the whole city.
## Replacing confidence interval with standard deviation
Instead of visualising a confidence interval, we may want to see how varied the measurements of nitrogen dioxide are across the different collection stations at a given point in time. To visualise this, set the "ci" parameter equal to the string "sd" to make the shaded area represent the standard deviation, which shows the spread of the distribution of observations at each x value.
```Python
sns.relplot(x="hour", y="NO_2", data=air_df, kind="line"
			ci="sd")
plt.show()
```
We can also turn off the confidence interval by setting the "ci" parameter equal to "None".
```Python
sns.relplot(x="hour", y="NO_2", data=air_df, kind="line"
			ci=None)
plt.show()
```
## Let's practice!
Alright, time to practice what we've learned!