Welcome back! In this last chapter we'll start discussing `merge_ordered()`. This method can merge time-series and other ordered data.
## `merge_ordered()`
The merge_ordered method will allow us to merge the left and right tables shown here. We can see the output of the merge when we merge on the "C" column. The results are similar to the standard merge method with an outer join, but here that the results are sorted. The sorted results make this a useful method for ordered or time-series data.
## Method comparison
So, let's first give context to this method. It has many of the same arguments we have already covered with the merge method. They both contain arguments to allow us to merge two tables on different columns. Both methods support different types of joins. Although, the default for the merge method is "inner", it is "outer" for merge_order method. Also, both methods support suffixes for overlapping column names. However, how you call each of the methods is different. Earlier in the course, we called the merge method by first listing a table and calling the method afterward. For merge_ordered(), you'll need to first call pandas then merge_ordered(). Let's look at an example.

| `.merge()` method                                                              | `merge_ordered()` method                                                       |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ |
| - Column(s) to join on<br> - `on`, `left_on`, and `right_on`                   | - Column(s) to join on<br> - `on`, `left_on`, and `right_on`                   |
| - Type of join<br> - `how` (left, right, inner, outer)<br> - **default** inner | - Type of join<br> - `how` (left, right, inner, outer)<br> - **default** outer |
| - Overlapping column names<br> - `suffixes`                                    | - Overlapping column names<br> - `suffixes`                                    |
| - Calling the method<br> - `df1.merge(df2)`                                    | - Calling the function<br> - `pd.merge_ordered(df1, df2)`                      |
In this chapter, we will be working with financial, macroeconomic, and stock market data.
## Stock data
In this example, we have a table of the stock prices of the Apple corporation from February to June 2007. We also have a table of the stock price for McDonald's corporation from January to May 2007, and we want to merge them.

The first two arguments are the left and right tables. We set the "on" argument equal to date. Finally, we set the suffixes argument to determine which table the data originated. This results in a table sorted by date. 
```Python
import pandas as pd
pd.merge_ordered(aapl, mcd, on='date', suffixes=('_aapl', '_mcd'))
```
There isn't a value for Apple in January or a value for McDonald's for June since values for these time periods are not available in the two original tables.
## Forward fill
We can fill in this missing data using a technique called forward filling. It will interpolate missing data by filling the missing values with the previous value. In the table shown here, the second and fourth rows of column B are filled with the values of B in the rows proceeding them.
```Python
pd.merge_order(aapl, mcd, on='date',
			   suffixes=('_aapl', '_mcd'),
			   fill_method='ffill')
```
Going back to our stock example from before, we now set the fill_method argument to "ffill" for forward fill. In the result, notice that the missing value for McDonald's in the last row is now filled in with the row before it. The table from before is shown on the right for easier comparison. Notice the missing value for Apple in the first row is still missing since there isn't a row before the first row to copy into the missing value for Apple.
## When to use `merge_ordered()`
You might think about using the merge_ordered method instead of the regular merge method when you are working with order or time-series data like in our example. Additionally, the fill forward feature is useful for handling missing data, as most machine learning algorithms require that there are no missing values.
## Let's practice!
Time to practice using the method and add it to your toolbox!