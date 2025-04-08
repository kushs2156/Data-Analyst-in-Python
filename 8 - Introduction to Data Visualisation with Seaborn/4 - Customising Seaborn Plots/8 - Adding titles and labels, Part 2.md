Hello! In this lesson, we'll continue learning how to customize plot titles and axis labels.
## Adding a title to AxesSubplot
In the last lesson, we learned how to add a title to a FacetGrid object using `g.fig.suptitle()`. To add a title to an AxesSubplot object like that from the "box plot" function, assign the plot to a variable and use `g.title()`. You can also use the “y” parameter here to adjust the height of the title.
```Python
g = sns.boxplot(x="Region", y="Birthrate", data=gdp_data)

g.set_title("New Title", y=1.03)
```
## Titles for subplots
Now let's look at what happens if the figure has subplots. Let's say we've divided countries into two groups - group one and group two - and we've set "col" equal to "Group" to create a subplot for each group. Since g is a FacetGrid object, using "g.fig.suptitle" will add a title to the figure as a whole. To alter the subplot titles, use `g.set_titles()` to set the titles for each AxesSubplot. If you want to use the variable name in the title, you can use "col name" in braces to reference the column value. Here, we've created subplot titles that display as "this is group 2" and "this is group 1".
```Python
g = sns.catplot(x="Region", y="Birthdate", data=gdp_data,
				kind="box", col="Group")

g.fig.suptitle("New Title", y=1.03)

g.set_titles("This is {col_name}")

plt.show()
```
## Adding axis labels
To add axis labels, assign the plot to a variable and then call the "set" function. Set the parameters "x label" and "y label" to set the desired x-axis and y-axis labels, respectively. This works with both FacetGrid and AxesSubplot objects.
```Python
g = sns.catplot(x="Region", y="Birthdate", data=gdp_data,
				kind="box")

g.set(xlabel="New X Label",
	  ylabel="New Y Label")

plt.show()
```
## Rotating x-axis tick labels
Sometimes, like in the example we've seen in this lesson, your tick labels may overlap, making it hard to interpret the plot. One way to address this is by rotating the tick labels. To do this, we don't call a function on the plot object itself. Instead, after we create the plot, we call the matplotlib function `plt.xticks()` and set "rotation" equal to 90 degrees. This works with both FacetGrid and AxesSubplot objects.
```Python
g = sns.catplot(x="Region", y="Birthdate", data=gdp_data,
				kind="box")

plt.xticks(rotation=90)
plt.show()
```
## Let's practice!
And that's it! Now it's time to create some clear and informative visualisations!