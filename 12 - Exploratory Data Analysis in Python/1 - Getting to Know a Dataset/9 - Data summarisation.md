We ended the last video by exploring data by genre, noticing that children's books in our dataset have slightly later publishing years in general.
## Exploring groups of data
We can explore the characteristics of subsets of data further with the help of the `.groupby()` function, which groups data by a given category, allowing the user to chain an aggregating function like .mean or .count to describe the data within each group. For example, we can group the books data by genre by passing the genre column name to the groupby function. Then, we chain an aggregating function, in this case, .mean, to find the mean value of the numerical columns for each genre. The results show that children's books have a higher average rating than other genres.
```Python
books.groupby("genre").mean()
```
## Aggregating functions
Other aggregating functions that are useful to chain with .groupby are `.sum`, `.count`, `.min`, `.max`, `.var`, which returns the variance, and `.std`, which returns the standard deviation.
## Aggregating ungrouped data
The `.agg()` function, short for aggregate, allows us to apply aggregating functions. By default, it aggregates data across all rows in a given column and is typically used when we want to apply more than one function. Here, we apply .agg to the books DataFrame and pass a list of aggregating functions to apply: .mean and .std. 
```Python
books.agg(["mean", "std"])
```
Our code returns a DataFrame of aggregated results, and .agg applies these functions only to numeric columns; the rating and year columns in the books DataFrame.
## Specifying aggregations for columns
We can even use a dictionary to specify which aggregation functions to apply to which columns. The keys in the dictionary are the columns to apply the aggregation, and each value is a list of the specific aggregating functions to apply to that column.
```Python
books.agg({"rating": ["mean", "std"], "year": ["median"]})
```
## Named summary columns
By combining .agg and .groupby, we can apply these new exploration skills to grouped data. Maybe we'd like to show the mean and standard deviation of rating for each book genre along with the median year. We can create named columns with our desired aggregations by using the dot-agg function and creating named tuples inside it. Each named tuple should include a column name followed by the aggregating function to apply to that column. The name of the tuple becomes the name of the resulting column. 
```Python
books.groupby("genre").agg(
	mean_rating=("rating", "mean"),
	std_rating=("rating", "std"),
	median_year=("year", "median")
)
```
Now, we can get two summary values of interest about ratings and our year data looks cleaner! We can see that the Fiction genre has the lowest average rating as well as the largest variation in ratings.
## Visualising categorical summaries
We can display similar information visually using a barplot. In Seaborn, bar plots will automatically calculate the mean of a quantitative variable like rating across grouped categorical data, such as the genre category we've been looking at. In Seaborn, bar plots also show a 95% confidence interval for the mean as a vertical line on the top of each bar. Here, we pass the genre column as the x values and the rating column as the y values. 
```Python
sns.barplot(data=books, x="genre", y="rating")
plt.show()
```
The results reinforce what we saw in the last slide: while Fiction books have the lowest rating, their ratings also have a little more variation.
## Let's show
Alright, it's time to summarise the unemployment data in the exercises.