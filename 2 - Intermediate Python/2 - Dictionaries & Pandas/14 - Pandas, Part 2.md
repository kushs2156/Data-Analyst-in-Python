In the previous video, we created the DataFrame brics containing basic data on the BRICS countries. The code here makes sure that the rows and columns are given appropriate labels. This is important to make accessing columns, rows and single elements in your DataFrame easy. Now that's exactly what I'll show you in this video, what a coincidence!
## Index and select data
There are numerous ways in which you can index and select data from DataFrames, so we'll take this step by step. First, I'm going to talk about how to use square brackets; next, I'm going to tell you about advanced data access methods, loc and iloc, that make Pandas extra powerful.
## Column Access []
Suppose that you only want to select the country column from brics. How to do this with square brackets? Well, you type brics, and then the column label inside square brackets. Python prints out the entire column, together with the row labels. 
```Python
brics["country"]
```
But there's something strange here. The last line says `Name: country, dtype: object`. We're clearly not dealing with a regular DataFrame here. Let's find out about the type of the object that gets returned, with the type function, with the type function, as follows. 
```Python
type(brics["country"])
>>pandas.core.series.Series
```
Okay, so we're dealing with a Pandas Series here. In a simplified sense, you can think of the Series as a 1-dimensional array that can be labelled, just like the DataFrame. Otherwise put, if you paste together a bunch of Series, you can create a DataFrame.

If you want to select the country column but keep the data in a DataFrame, you'll need double square brackets, like this. 
```Python
brics[["country"]]
```
If you check out the type of this fellow, it's a good old DataFrame, this time with only one column though.
```Python
type(brics[["country"]])
>>pandas.core.frame.DataFrame
```

You can perfectly extend this call to select two columns, country and capital, for example. 
```Python
brics[["country", "capital"]]
```
If you look at it from a different angle, you're actually putting a list with column labels inside another set of square brackets, and end up with a 'sub DataFrame', containing only the country and capital columns. You can also use the same square brackets to select rows from a DataFrame.
## Row Access
The way to do it is by specifying a slice. To get the second, third and fourth rows of brics, we use the slice 1 colon 4. Remember that the end of the slice is exclusive and that the index starts at zero.
```Python
brics[1:4]
```
These square brackets work, but it only offers limited functionality. Ideally, we'd want something similar to 2D NumPy arrays. There, you also used square brackets, the index or slice before the comma referred to the rows, the index or slice after the comma referred to the columns: `my_array[rows, columns]`. If we want to do a similar thing with Pandas, we have to extend our toolbox with the `loc` and `iloc` functions. loc is a technique to select parts of your data based on labels, iloc is position based. Let's start with loc first.
## Row Access loc
Let's have another look at the brics DataFrame, and try to get the row for Russia. This is how it's done. You put the label of the row of interest in square brackets after loc. Again, we get a Pandas Series, containing all the row's information, rather inconveniently shown on different lines.
```Python
brics.loc["RU"]
```
To get a DataFrame, we have to put the "RU" string inside another pair of brackets.
```Python
brics.loc[["RU"]]
```
We can also select multiple rows at the same time. Suppose you want to also include India and China. This will do the trick; simply add some more row labels to the list. 
```Python
brics.loc[["RU", "IN", "CH"]]
```
This was only selecting entire rows, that's something you could also do with the basic square brackets. The difference here is that you can extend your selection with a comma and a specification of the columns of interest.
## Row & Column loc
Let's extend the previous call to only include the country and capital columns. We add a comma, and a list of column labels we want to keep. The intersection gets returned. 
```Python
brics.loc[["RU", "IN", "CH"], ["country", "capital"]]
```
Of course, you can also use loc to select all rows but only a specific number of columns. Simply replace the first list that specifies the row labels with a colon, a slice going from beginning to end. This time, the intersection spans all rows, but only two columns.
```Python
brics.loc[:, ["country", "capital"]]
```
## Recap
So, let's take a step back: simple square brackets work fine if you want to get columns; to get rows, you can use slicing. The loc function is more versatile: you can select rows, columns, but also rows and columns at the same time. When you use loc, subsetting becomes remarkable similar to how you subsetted 2D NumPy arrays. The only difference is that you use row labels with loc, not the positions of the elements. If you want to subset Pandas DataFrames based on their position, or index, you'll need the iloc function.
## Row Access iloc
Let's cover the same examples as with loc, and start with getting the row for Russia. In loc, you use the "RU" string in double square brackets, to get a DataFrame, like here. In iloc, you use the index 1 instead of RU. The results are exactly the same.
```Python
brics.iloc[[1]]
```
To get the rows for Russia, India and China, which was coded like this when using loc, you can now use a list with the index 1 to 3. Again, the same result.
```Python
brics.iloc[[1,2,3]]
```
## Row & Column iloc
To in addition only keep the country and capital column, which we did as follows with loc, we put the indexes 0 and 1 in a list after the comma, referring to the country and capital column.
```Python
brics.iloc[[1,2,3], [0,1]]
```
Finally, you can keep all rows and keep only the country and capital column in a similar fashion. With loc, this is how it's done.
```Python
brics.iloc[:, [0,1]]
```
For iloc, it's like this. loc and iloc are pretty similar, the only difference is how you refer to columns and rows. I know all of this could be a lot to take in, so lets get you coding yourself to master indexing and selecting data. Keep learning by doing!