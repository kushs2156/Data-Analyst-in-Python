Hi, I'm Maggie, and I'll be the other instructor for this course. In the first chapter, you learned about DataFrames, how to sort and subset them, and how to add new columns to them. In this chapter, we'll talk about aggregating data, starting with summary statistics. Summary statistics, as follows from their name, are numbers that summarise and tell you about your dataset.

One of the most common summary statistics for numeric data is the mean, which is one way of telling you where the "centre" of your data is. You can calculate the mean of a column by selecting the column with square brackets and calling `.mean()`. There are lots of other summary statistics that you can compute on columns, like `.median()` and `.mode()`, `.min()` and `.max()`, and `.var()` and `.std()`. You can also take sums (`.sum()`) and calculate quantiles (`.quantile()`).

You can also get summary statistics for date columns. For example, we can find the oldest dog's date of birth by taking the minimum of the date of birth column. Similarly, we can take the maximum to see that the youngest dog was born in 2018.
## The .agg() method
The aggregate, or agg, method allows you to compute custom summary statistics. Here, we create a function called pct30 that computes the thirtieth percentile of a DataFrame column. 
```Python
def pct30(column):
	return column.quantile(0.3)

dogs["weight_kg"].agg(pct30)
>>22.5999999998
```
Don't worry if this code doesn't make sense to you -- just know that the function takes in a column and spits out the column's thirtieth percentile. Now we can subset the weight column and call dot-agg, passing in the name of our function, pct30. It gives us the thirtieth percentile of the dogs' weights.

agg can also be used on more than one column. By selecting the weight and height columns before calling agg, we get the thirtieth percentile for both columns.
```Python
dogs[["weight_kg", "height_cm"]].agg(pct30)
>>weight_kg     22.6
>>height_cm     45.4
>>dtype: float64
```

We can also use agg to get multiple summary statistics at once. Here's another function that computes the fortieth percentile called pct40. We can pass a list of functions into agg, in this case, pct30 and pct40, which will return the thirtieth and fortieth percentiles of the dogs' weights.
```Python
def pct40(column):
	return column.quantile(0.4)

dogs["weight_kg"].agg([pct30, pct40])
>>pct30   22.6
>>pct40   24.0
>>Name: weight_kg, dtype: float64
```
## Cumulative sum
pandas also has methods for computing cumulative statistics, for example, the cumulative sum. Calling `.cumsum()` on a column returns not just one number, but a number for each row of the DataFrame. The first number returned, or the number in the zeroth index, is the first dog's weight. The next number is the sum of the first and second dogs' weights. The third number is the sum of the first, second, and third dogs' weights, and so on. The last number is the sum of all the dogs' weights.
```Python
dogs["weight_kg"]
>>0   24
>>1   24
>>2   24
>>...

dogs["weight_kg"].cumsum()
>>0   24
>>1   48
>>2   72
>>...
```

pandas also has methods for other cumulative statistics, such as the cumulative maximum (`.cummax()`), cumulative minimum (`.cummin()`), and the cumulative product (`.cumprod()`). These all return an entire column of a DataFrame, rather than a single number.
## Walmart
In this chapter, you'll be working with data on Walmart stores, which is a chain of department stores in the US. The dataset contains weekly sales in US dollars in various stores. Each store has an ID number and a specific store type. The sales are also separated by department ID. Along with weekly sales, there is information about whether it was a holiday week or not, the average temperature during the week in that location, the average fuel price in dollars per litre that week, and the national unemployment rate that week.
## Let's practice!
Time to practice your summary statistics skills!