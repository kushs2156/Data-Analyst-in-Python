We saw in the last lesson that a really nice advantage of Seaborn is that it works well with pandas DataFrames. In this lesson, we'll see another big advantage that Seaborn offers: the ability to quickly add a third variable to your plots by adding colour. 

To showcase this cool feature in Seaborn, we'll be using Seaborn's built-in tips dataset. You can access it by using the `load_dataset()` function in Seaborn and passing in the name of the dataset. 
```Python
import pandas as pd
import seaborn as sns
tips = sns.load_dataset("tips")
tips.head()
```
These are the first five rows of the tips dataset. This dataset contains one row for each table served at a restaurant and has information about things like the bill amount, how many people were at the table, and when the table was served. Let's explore the relationship between the "total_bill" and "tip" columns using a scatter plot.
## A basic scatter plot
Here is the code to generate it. The total bill per table (in dollars) is on the x-axis, and the total tip (in dollars) is on the y-axis. 
```Python
sns.scatterplot(x="total_bill", y="tip", data=tips, hue="smoker")
plt.show()
```
We can see from this plot that larger bills are associated with larger tips. What if we want to see which of the data points are smokers versus non-smokers? Seaborn makes this super easy. You can set the "hue" parameter equal to the DataFrame column name "smoker" and then Seaborn will automatically color each point by whether they are a smoker. Plus, it will add a legend to the plot automatically! If you don't want to use pandas, you can set it equal to a list of values instead of a column name.

Hue also allows you to assert more control over the ordering and colouring of each value. The `hue_order` parameter takes in a list of values and will set the order of the values in the plot accordingly. Notice how the legend for smoker now lists "yes" before "no".
```Python
sns.scatterplot(x="total_bill", y="tip", data=tips, 
				hue="smoker", hue_order=["Yes", "No"])
plt.show()
```
## Specifying hue colours
You can also control the colours assigned to each value using the `palette` parameter. This parameter takes in a dictionary, which is a data structure that has key-value pairs. This dictionary should map the variable values to the colours you want to represent the value. Here, we create a dictionary called "hue_colors" that maps the value "Yes" to the colour black and the value "No" to the colour red. When we set hue equal to "smoker" and the palette parameter equal to this dictionary, we have a scatter plot where smokers are represented with black dots and non-smokers are represented with red dots.
```Python
hue_colors = {"Yes": "black",
			  "No": "red"}

sns.scatterplot(x="total_bill", y="tip", data=tips, 
				hue="smoker", palette=hue_colors)
plt.show()
```
## Colour options
In the last example, we used the words "black" and "red" to define what the hue colours should be. This only works for a small set of colour names that are defined by Matplotlib. Here is the list of Matplotlib colours and their names. Note that you can use a single-letter Matplotlib abbreviation instead of the full name. You can also use an HTML colour hex code instead of these Matplotlib colour names, which allows you to choose any colour you want to.
![[Pasted image 20250221210933.png]]
Here's an example using HTML hex codes. Make sure you put the hex codes in quotes with a hash sign at the beginning.
```Python
hue_colors = {"Yes": "#808080",
			  "No": "#00FF00"}

sns.scatterplot(x="total_bill", y="tip", data=tips, 
				hue="smoker", palette=hue_colors)
plt.show()
```
## Using hue with count plots
As a final note, hue is available in most of Seaborn's plot types. For example, this count plot shows the number of observations we have for smokers versus non-smokers, and setting "hue" equal to "sex" divides these bars into subgroups of males versus females. 
```Python
sns.countplot(x="smoker", data=tips, hue="sex")
plt.show()
```
From this plot, we can see that males outnumber females among both smokers and non-smokers in this dataset.
## Let's practice!
We'll be using hue a lot in this course, so let's practice what we've learned to round out the first chapter!