In this course, we've learned a great deal about how to create effective data visualisations in Seaborn. In this lesson, we'll review what we've learned and connect the pieces together to form a cohesive picture of how to use Seaborn for future projects.
## Getting started
The first thing to recall is simply how to import Seaborn and its related library, Matplotlib. To do this, write `import seaborn as sns` and `import matplotlib.pyplot as plt`. Recall also that at the end of your data visualisation code, you'll call `plt.show()` to show the visualisation.
## Relational plots
After you've imported the appropriate libraries, the next thing to do is to choose what type of plot you want to create. Relational plots are plots that show the relationship between two quantitative variables. Examples of relational plots that we've seen in this course are scatter plots and line plots. You can create a relational plot using "relplot()" and providing it with the x-axis variable name, y-axis variable name, the pandas tidy DataFrame, and the type of plot (either scatter or line).
## Categorical plots
Categorical plots are another type of plot. These describe the distribution of a quantitative variable within categories given by a categorical variable. Examples of categorical plots we've seen are bar plots, count plots, box plots, and point plots. You can create a categorical plot using "catplot()" and providing it with the x-axis variable name, y-axis variable name (if applicable), the pandas tidy DataFrame, and the type of plot (either bar, count, box, or point).
## Adding a third variable (hue)
If we want to add a third dimension to our plots, we can do this in one of two ways. Setting the "hue" parameter to a variable name will create a single plot but will show subgroups that are different colours based on that variable's values.
## Adding a third variable (row/col)
Alternatively, you can use "relplot()" and "catplot()"’s "col" and "row" parameters to graph each subgroup on a separate subplot in the figure.
## Customisation
Once you have the basic plot created, you might want to customise the plot's appearance to improve its readability. You can change the background of the plot using `sns.set_style()`, the colour of the main elements using `sns.set_palette()`, and the scale of the plot using `sns.set_context()`.
## Adding a title
Finally, every plot should be given an informative title and axis labels. Recall the two types of plot objects - FacetGrids and AxesSubplots - and the way to add a title to each of them.

| Object Type   | Plot Types                              | How to Add Title   |
| ------------- | --------------------------------------- | ------------------ |
| `FacetGrid`   | `relplot()`, `catplot()`                | `g.fig.suptitle()` |
| `AxesSubplot` | `scatterplot()`, `countplot()`,<br>etc. | `g.set_title()`    |
## Final touches
Also recall how to use the "set" function with the "xlabel" and "ylabel" parameters to provide custom x- and y-axis labels, and how to use "plt.xticks" with the "rotation" parameter to rotate the x-tick labels.
## Let's practice!
And that's it! You're now equipped to make impressive and effective data visualisations with Seaborn. Let's practice putting all of these steps together in the final exercises of this course.