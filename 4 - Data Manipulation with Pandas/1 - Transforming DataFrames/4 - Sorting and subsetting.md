In this video, we'll cover the two simplest and possibly most important ways to find interesting parts of your DataFrame.
## Sorting
The first thing you can do is change the order of the rows by sorting them so that the most interesting data is at the top of the DataFrame. You can sort rows using the ==`sort_values()`== method, passing in a column name that you want to sort by. For example, when we apply sort_values on the weight_kg column of the dogs DataFrame, we get the lightest dog at the top, Stella the Chihuahua, and the heaviest dog at the bottom, Bernie the Saint Bernard.
```Python
dogs.sort_values("weight_kg")
```
Setting the ascending argument to False will sort the data the other way around, from heaviest dog to lightest dog.
```Python
dogs.sort_values("weight_kg", ascending=False)
```
We can sort by multiple variables by passing a list of column names to sort_values. Here, we sort first by weight, then by height. Now, Charlie, Lucy, and Bella are ordered from shortest to tallest, even though they all weigh the same.
```Python
dogs.sort_values(["weight_kg", "height_cm"])
```
To change the direction values are sorted in, pass a list to the ascending argument to specify which direction sorting should be done for each variable. Now, Charlie, Lucy, and Bella are ordered from tallest to shortest.
```Python
dogs.sort_values(["weight_kg", "height_cm"], ascending=[True, False])
```
## Subsetting columns
We may want to zoom in on just one column. We can do this using the name of the DataFrame, followed by square brackets with a column name inside. Here, we can look at just the name column: `dogs["name"]`. To select multiple columns, you need two pairs of square brackets. 
```Python
dogs[["breed", "height_cm"]]

cols_to_subset = ["breed", "height_cm"]
dogs[cols_to_subset]
```
In this code, the inner and outer square brackets are performing different tasks. The outer square brackets are responsible for subsetting the DataFrame, and the inner square brackets are creating a list of column names to subset. This means you could provide a separate list of column names as a variable and then use that list to perform the same subsetting. Usually, it's easier to do in one line.
## Subsetting rows
There are lots of different ways to subset rows. The most common way to do this is by creating a logical condition to filter against. For example, let's find all the dogs whose height is greater than 50 centimetres. Now we have a True or False value for every row.
```Python
dogs["height_cm"] > 50

dogs[dogs["height_cm"] > 50]
```
We can use the logical condition inside of square brackets to subset the rows we're interested in to get all of the dogs taller than 50 centimetres. We can also subset rows based on text data. Here, we use the double equal sign in the logical condition to filter the dogs that are Labradors.
```Python
dogs[dogs["breed"] == "Labrador"]
```

We can also subset based on dates. Here, we filter all the dogs born before 2015. Notice that the dates are in quotes and are written as year then month, then day. This is the international standard date format.
```Python
dogs[dogs["date_of_birth"] < "2015-01-01"]
```
## Subsetting based on multiple conditions
To subset the rows that meet multiple conditions, you can combine conditions using logical operators, such as the "and" operator seen here. This means that only rows that meet both of these conditions will be subsetted. You could also do this in one line of code, but you'll also need to add parentheses around each condition.
```Python
is_lab = dogs["breed"] == "Labrador"
is_brown = dogs["color"] == "Brown"
dogs[is_lab & is_brown]

dogs[ (dogs["breed"] == "Labrador") & (dogs["color"] == "Brown") ]
```
## Subsetting using .isin()
If you want to filter on multiple values of a categorical variable, the easiest way is to use the ==`isin()`== method. This takes in a list of values to filter for. Here, we check if the colour of a dog is black or brown, and use this condition to subset the data.
```Python
is_black_or_brown = dogs["color"].isin(["Black", "Brown"])
dogs[is_black_or_brown]
```
## Let's practice!
Now it's time to practice your sorting and subsetting!