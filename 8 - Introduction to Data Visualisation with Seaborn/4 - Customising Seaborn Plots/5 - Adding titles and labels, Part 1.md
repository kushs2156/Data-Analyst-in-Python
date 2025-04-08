Welcome! In the next two lessons, we'll go over one of the most important parts of any data visualisation: plot titles and axis labels.
## Creating informative visualisations
We create data visualisations to communicate information, and we can't do that effectively without a clear title and informative axis labels. To see this, let's compare two versions of the same visualisation. On the left, we see box plots showing the distribution of birth rates for countries in each of 11 regions. On the right, we see the same visualisation with three key modifications to make it easier to understand. A title is added, which immediately orients the audience to what they're looking at. The axis labels are more informative, making it clearer that birth rate is measured per one thousand people and birth rates are measured per country in each region. Finally, the x-axis tick labels are rotated to make it clear what each region is called. Let's learn how to make these changes.
## FacetGrid vs. AxesSubplot objects
Before we go into the details of adding a title, we need to understand an underlying mechanism in Seaborn. Seaborn's plot functions create two different types of objects: FacetGrids and AxesSubplots. To figure out which type of object you're working with, first assign the plot output to a variable. In the documentation, the variable is often named "g", so we'll do that here as well. Write "type" "g" to return the object type. This scatter plot is an AxesSubplot.
```Python
g = sns.scatterplot(x="height", y="weight", data=df)
type(g)
>> matplotlib.axes._subplots.AxesSubplot
```
## An empty FacetGrid
A **FacetGrid consists of one or more AxesSubplots**, which is how it supports subplots.
## FacetGrid vs. AxesSubplot objects
Recall that "relplot()" and "catplot()" both support making subplots. This means that they are creating FacetGrid objects. In contrast, single-type plot functions like "scatterplot()" and "countplot()" return a single AxesSubplot object.
## Adding a title to FacetGrid
Let's return to our messy plot from the beginning. Recall that "catplot()" enables subplots, so it returns a FacetGrid object. To add a title to a FacetGrid object, first assign the plot to the variable "g". After you assign the plot to "g", you can set the title using `g.fig.suptitle()`. This tells Seaborn you want to set a title for the figure as a whole.
```Python
g = sns.catplot(x="Region", y="Birthrate", data=gdp_data,
				kind="box")
g.fig.suptitle("New Title",
			   y=1.03)
plt.show()
```
Note that by default, the figure title might be a little low. To adjust the height of the title, you can use the "y" parameter. The default value is 1, so setting it to 1 point 03 will make it a little higher than the default.
## Let's practice!
We'll learn how to add a title to an AxesSubplot object in the next lesson. For now, let's pause and practice what you just learned!