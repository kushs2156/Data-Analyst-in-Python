Pivot tables are another way of calculating grouped summary statistics. If you've ever used a spreadsheet, chances are you've used a pivot table. Let's see how to create pivot tables in pandas.
## Groupby to pivot table
In the last lesson, we grouped the dogs by colour and calculated their mean weights. We can do the same thing using the `.pivot_table()` method. The "values" argument is the column that you want to summarise, and the index column is the column that you want to group by. By **default**, **pivot_table** takes the **mean** value for each group.
```Python
dogs.pivot_table(values="weight_kg", index="color")
```
If we want a different summary statistic, we can use the aggfunc argument and pass it a function. Here, we take the median for each dog colour using NumPy's median function.
```Python
dogs.pivot_table(values="weight_kg", index="color", aggfunc=np.median)
```
To get multiple summary statistics at a time, we can pass a list of functions to the aggfunc argument. Here, we get the mean and median for each dog colour.
```Python
dogs.pivot_table(values="weight_kg", index="color", 
				 aggfunc=[np.mean, np.median])
```
## Pivot on two variables
You also previously computed the mean weight grouped by two variables: colour and breed. We can also do this using the pivot_table method. To group by two variables, we can pass a second variable name into the columns argument. While the result looks a little different than what we had before, it contains the same numbers. There are NaNs, or missing values, because there are no black Chihuahuas or gray Labradors in our dataset, for example.
```Python
dogs.pivot_table(values="weight_kg", index="color", columns="breed")

dogs.pivot_table(values="weight_kg", index="color", 
				 columns="breed", fill_value=0)
```
Instead of having lots of missing values in our pivot table, we can have them filled in using the `fill_value` argument. Here, all of the NaNs get filled in with zeros.
## Summing with pivot tables
If we set the `margins` argument to True, the last row and last column of the pivot table contain the mean of all the values in the column or row, not including the missing values that were filled in with 0s. 
```Python
dogs.pivot_table(values="weight_kg", index="color", columns="breed",
				 fill_value=0, margins=True)
```
For example, in the last row of the Labrador column, we can see that the mean weight of the Labradors is 26 kilograms. In the last column of the Brown row, the mean weight of the Brown dogs is 24 kilograms. The value in the bottom right, in the last row and last column, is the mean weight of all the dogs in the dataset. Using margins equals True allows us to see a summary statistic for multiple levels of the dataset: the entire dataset, grouped by one variable, by another variable, and by two variables.
## Let's practice!
Time to practice aggregating data using pivot tables!
