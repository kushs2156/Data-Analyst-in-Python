Hello there! In this lesson, we'll talk about how to connect two tables vertically. So far in this course, we have only discussed how to merge two tables, which mainly grows them horizontally. But what if we wanted to grow them vertically? We can use the `.concat()` method to concatenate, or stick tables together, vertically or horizontally, but in this lesson, we'll focus on vertical concatenation.
## Basic concatenation
Often, data for different periods of time will come in multiple tables, but if we want to analyse it together, we'll need to combine them into one. Here are three separate tables of invoice data from our streaming service. Notice the column headers are the same. The separate tables are named "inv" underscore Jan through March. We can pass a list of table names into pandas `.concat()` to combine the tables in the order they're passed in. To concatenate vertically, the axis argument should be set to 0, but 0 is the default, so we don't need to explicitly write this. The result is a vertically combined table. Notice each table's index value was retained.
```Python
pd.concat([inv_jan, inv_feb, inv_mar], ignore_index=True)
```
If the index contains no valuable information, then we can ignore it in the concat method by setting `ignore_index = True`. The result is that the index will go from 0 to n-1.
## Setting labels to original tables
Now, suppose we wanted to associate specific keys with each of the pieces of our three original tables. We can provide a list of labels to the keys argument. Make sure that ignore_index argument is False, since you ==can't add a key and ignore the index at the same time==. This results in a table with a multi-index, with the label on the first level.
```Python
pd.concat([inv_jan, inv_feb, inv_mar], ignore_index=False,
		   keys=['jan', 'feb', 'mar'])
```
## Concatenate tables with different column names
What if we need to combine tables that have different column names? The "inv_feb" table now has a column added for billing country. The concat method by default will include all of the columns in the different tables it's combining. The sort argument, if true, will alphabetically sort the different column names in the result. We can see in the results that the billing country for January invoices is NaN. However, there are values for the February invoices.
```Python
pd.concat([inv_jan, inv_feb], sort=True)
```
If we only want the matching columns between tables, we can set the join argument to "inner". Its default value is equal to "outer", which is why concat by default will include all of the columns. Additionally, the sort argument has no effect when join equals "inner". The order of the columns will be the same as the input tables. Now the bill country column is gone and we're only left with the columns the tables have in common.
```Python
pd.concat([inv_jan, inv_feb], join='inner')
```
## Let's practice!
With that, let's get some practice in!