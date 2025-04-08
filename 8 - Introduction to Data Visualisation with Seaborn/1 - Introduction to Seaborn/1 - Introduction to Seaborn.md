So what is Seaborn? Seaborn is a powerful Python library for creating data visualisations. It was developed in order to make it easy to create the most common types of plots. The plot shown here can be created with just a few lines of Seaborn code.

![[Pasted image 20250221201604.png]]

This is a picture of a typical data analysis workflow. Data visualisation is often a huge component of both the data exploration phase and the communication of results, so Seaborn will be very useful there.
## Advantages of Seaborn
There are several tools that can be used for data visualisation, but Seaborn offers several advantages. First, Seaborn's main purpose is to make data visualisation easy. It was built to automatically handle a lot of complexity behind the scenes. Second, Seaborn works extremely well with pandas data structures. pandas is a Python library that is widely used for data analysis. Finally, it's built on top of Matplotlib, which is another Python visualisation library. Matplotlib is extremely flexible. Seaborn allows you to take advantage of this flexibility when you need it, while avoiding the complexity that Matplotlib's flexibility can introduce.
## Getting started
To get started, we'll need to import the Seaborn library. The line `import seaborn as sns` will import Seaborn as the conventionally used alias "sns". Why "sns"? The Seaborn library was apparently named after a character named Samuel Norman Seaborn from the television show "The West Wing" - thus, the standard alias is the character's initials ("sns"). We also need to import Matplotlib, which is the library that Seaborn is built on top of. We do this by typing `import matplotlib.pyplot as plt`. "plt" is the alias that most people use to refer to Matplotlib, so we'll use that here as well.
## Example 1: Scatter plot
Let's now dive into an example to illustrate how easily you can create visualisations using Seaborn. Here, we have data for 10 people consisting of lists of their heights in inches and their weights in pounds. Do taller people tend to weigh more? You can visualise this using a type of plot known as a scatter plot, which you'll learn more about later in the course. Use `sns.scatterplot()` to call the scatterplot function from the Seaborn library. Then, specify what to put on the x-axis and y-axis. Finally, call the `plt.show()` function from Matplotlib to show the scatterplot. This plot shows us that taller people tend to have a higher weight.
```Python
import seaborn as sns
import matplotlib.pyplot as plt

height = [62, 64, 69, 75, 66, 68, 65, 71, 76, 73]
weight = [120, 136, 148, 175, 137, 165, 154, 172, 200, 187]

sns.scatterplot(x=height, y=weight)
plt.show()
```
## Example 2: Create a count plot
How many of our observations of heights and weights came from males vs. females? You can use another type of plot - the count plot - to investigate this. Count plots take in a categorical list and return bars that represent the number of list entries per category. Use the `countplot()` function and provide the list of every person's gender. This count plot shows that out of the 10 observations we had in our height and weight scatter plot, 6 were male and 4 were female.
```Python
gender = ["Female", "Female", "Female", "Female", "Male",
		  "Male", "Male", "Male", "Male", "Male"]
sns.countplot(x=gender)
plt.show()
```
## Course preview
Now, those were a couple of simple examples. Throughout this course, you'll learn to make more complex visualisations such as those pictured here. More importantly, you'll learn when to use each type of visualisation in order to most effectively extract and communicate insights using data.
## Let's practice!
I'm excited to dive into Seaborn with you throughout this course. For now, let's practice what you've just learned!