Data validation is an important early step in EDA. We want to understand whether data types and ranges are as expected before we progress too far in our analysis! Let's dive in.
## Validating data types
We learned in the last lesson that `.info()` gives a quick overview of data types included in a dataset along with other information such as the number of non-missing values. We can also use the DataFrame `.dtypes` attribute if we're only interested in data types. But what if we aren't happy with these data types? Here, the year column in the books DataFrame is stored as a float, which doesn't make sense for year data, which should always be a whole number.
## Updating data types
Luckily, the `.astype()` function allows us to change data types without too much effort. Here, we redefine the year column by selecting the column and calling the .astype method, indicating we'd like to change the column to an integer. 
```Python
books["year"] = books["year"].astype(int)
```
Then we use the .dtypes attribute to check that the year column data is now stored as integers - and it is! Common programming data types as well as their Python names are listed here. It's the Python name that we pass to the astype function, as we did with int on the previous slide.

| Type       | Python Name |
| ---------- | ----------- |
| String     | `str`       |
| Integer    | `int`       |
| Float      | `float`     |
| Dictionary | `dict`      |
| List       | `list`      |
| Boolean    | `bool`      |
## Validating categorical data
We can validate categorical data by comparing values in a column to a list of expected values using `.isin()`, which can either be applied to a Series as we'll show here or to an entire DataFrame. Let's check whether the values in the genre column are limited to "Fiction" and "Non Fiction" by passing these genres as a list of strings to .isin. 
```Python
books["genre"].isin(["Fiction", "Non Fiction"])
```
The function returns a Series of the same size and shape as the original but with True and False in place of all values, depending on whether the value from the original Series was included in the list passed to .isin. We can see that some values are False. We can also use the tilde operator at the beginning of the code block to invert the True/ False values so that the function returns True if the value is NOT in the list passed to .isin.
```Python
~books["genre"].isin(["Fiction", "Non Fiction"])
```
And if we're interested in filtering the DataFrame for only values that are in our list, we can use the .isin code we just wrote to filter using Boolean indexing!
```Python
books[books["genre"].isin(["Fiction", "Non Fiction"])].head()
```
## Validating numerical data
Let's now validate numerical data. We can select and view only the numerical columns in a DataFrame by calling the `.select_dtypes()` method and passing "number" as the argument.
```Python
books.select_dtypes("number").head()
```
Perhaps we'd like to know the range of years in which the books in our dataset were published. We can check the lowest and highest years by using the .min and .max functions, respectively. 
```Python
books["year"].min()

books["year"].max()
```
And we can view a more detailed picture of the distribution of year data using Seaborn's boxplot function. 
```Python
sns.boxplot(data=books, x="year")
plt.show()
```
The boxplot shows the boundaries of each quartile of year data: as we saw using min and max, the lowest year is 2009 and the highest year is 2019. The 25th and 75th percentiles are 2010 and 2016 and the median year is 2013.

We can also view the year data grouped by a categorical variable such as genre by setting the y keyword argument. It looks like the children's books in our dataset have slightly later publishing years in general, but the range of years is the same for all genres.
```Python
sns.boxplot(data=books, x="year", y="genre")
```
## Let's practice!
Now it's your turn to validate the unemployment data!