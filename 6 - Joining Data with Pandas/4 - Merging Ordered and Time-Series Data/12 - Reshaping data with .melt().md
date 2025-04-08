In our last lesson of the course, let's talk about the `.melt()` method. This method will unpivot a table from wide to long format. This is often a much more computer-friendly format, therefore making this a valuable method to know.
## Wide versus long data
Sometimes we will come across data where every row relates to one subject, and each column has different information about an attribute of that subject. Data formatted in this way is often called wide. There are other times when the information about one subject is found over many rows, and each row has one attribute about that subject. Data formatted in this way is often called long or tall. In general, wide formatted data is easier to read by people than long formatted. However, long formatted data is often more accessible for computers to work with.

| *Wide Format* | first | last | height | weight |
| ------------- | ----- | ---- | ------ | ------ |
| 0             | John  | Doe  | 5.5    | 130    |
| 1             | Mary  | Bo   | 6.0    | 150    |

| *Long Format* | first | last | variable | value |
| ------------- | ----- | ---- | -------- | ----- |
| 0             | John  | Doe  | height   | 5.5   |
| 1             | Mary  | Bo   | height   | 6.0   |
| 2             | John  | Doe  | weight   | 130   |
| 3             | Mary  | Bo   | weight   | 150   |
## What does the `.melt()` method do?
The melt method will allow us to unpivot, or change the format of, our dataset. In this image, we change the height and weight columns from their wide horizontal placement to a long vertical placement. To demonstrate the melt method, let's start with this dataset of financial metrics of two popular social media companies. Notice that the years are horizontal. Let's change them so that they are vertically placed.

Here we call the melt() method on the table social_fin. The first input argument to the method is `id_vars`. These are columns to be used as identifier variables. We can also think of them as columns in our original dataset that we do not want to change. 
```Python
social_fin_tall = social_fin.melt(id_vars=['financial', 'company'])
print(social_fin_tall.head(10))
```
In our output, we print the first ten rows. Our years are listed vertically. Our final column now has all of our values in one column versus multiple columns. Again, this is a much more computer-friendly format than our original table. We unpivoted each of the separate columns 2016 through 2019. Our output has data for every year in our starting table, but again, we are only showing the first couple of rows. In the next example, we will look at how to control what columns are unpivoted.
## Melting with `value_vars`
This time, let's use the argument value_vars with the melt() method. This argument will allow us to control which columns are unpivoted. Here, we unpivot only the 2018 and 2017 columns. 
```Python
social_fin_tall = social_fin.melt(id_vars=['financial', 'company'],
								  values_vars=['2018','2017'])
print(social_fin_tall.head(9))
```
Our output now only has data for the years 2018 and 2017. Additionally, the order of the value_var was kept. The output starts with 2018, then moves to 2017. Finally, notice that the column with the years is now named variable, and our values column is named value. We will adjust that in our next example.
## Melting with column names
In this example, we have added some additional inputs to our melt() method. The var_name argument will allow us to set the name of the year column in the output. Similarly, the value_name argument will allow us to set the name of the value column in the output. We again print the first few rows of the output. 
```Python
social_fin_tall = social_fin.melt(id_vars=['financial', 'company'],
								  values_vars=['2018','2017'],
								  var_name='year', 
								  value_name='dollars')
print(social_fin_tall.head(9))
```
It is the same as before, except our variable and value columns are renamed year and dollars, respectively. We have seen how the melt() method is useful for reshaping our tables. Imagine a situation where you have merged many columns, making your table very wide. The melt() method can then be used to reshape that table into a more computer-friendly format.
## Let's practice
Alright, time to practice!