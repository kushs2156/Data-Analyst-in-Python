Welcome to this course on exploratory data analysis! I'm Izzy, and I'll be your coach for chapters one and three of this course. My friend and colleague George will guide you through chapters two and four.
## Exploratory Data Analysis
Let's say we've got a new dataset about books. Is this good data? What questions can it answer for us? It's only after we understand what our data contains that we can think about how the data might be useful to us. Exploratory Data Analysis, or EDA for short, is the process of cleaning and reviewing data to derive insights such as descriptive statistics and correlation and generate hypotheses for experiments. EDA results often inform the next steps for the dataset, whether that be generating hypotheses, preparing the data for use in a machine learning model, or even throwing the data out and gathering new data!
## A first look with `.head()`
Let's begin by importing a dataset and reviewing some useful pandas methods for initial exploration! We'll import the books data from a csv file using pd.read_csv and save it as a DataFrame called "books". Taking a look at the top of the DataFrame using the head function, we can see that our data contains columns representing book names, authors, ratings, publishing years, and genres.
## Gathering more `.info()`
pandas also offers a quick way to summarize the number of missing values in each column, the data type of each column, and memory usage using the .info method. It looks like there are no missing values in our dataset, but it does have a variety of data types.
## A closer look at categorical columns
A common question about categorical columns in a dataset is how many data points we have in each category. For example, perhaps we're interested in the genres represented in our books data. We can select the genre column and use the pandas Series method `.value_counts()` to find the number of books with each genre.
## `.describe()` numerical columns
Gaining a quick understanding of data included in numerical columns is done with the help of the `DataFrame.describe()` method. Calling .describe on books, we see that it returns the count, mean, and standard deviation of the values in each numerical column (in this case rating and year), along with the min, max, and quartile values.
## Visualising numerical data
Histograms are a classic way to look at the distribution of numerical data by splitting numerical values into discrete bins and visualising the count of values in each bin. Throughout this course, we'll use Seaborn to explore datasets visually. Seaborn is imported as sns. We'll also import matplotlib.pyplot aliased as plt. To create a histogram, we'll use sns.histplot and pass the books DataFrame as the data argument. Next, we indicate which column we'd like to use as x by passing the column name rating to the x keyword argument. After running plt.show() to display the plot, we see that most books received ratings above 4.4, with very few getting ratings below 4.0. However, the bin size here is a little awkward. Ideally, we would have a bin for each tenth of a rating, such as a single bin for scores greater than 4.5 to 4.6 inclusive. We can set a bin width of 0.1 using the binwidth keyword argument. That's better!
```Python
import matplotlib.pyplot as plt
import seaborn as sns

sns.histplot(data=books, x="rating", binwidth=0.1)
plt.show()
```
## Let's practice!
Let's explore a brand new dataset using these skills.