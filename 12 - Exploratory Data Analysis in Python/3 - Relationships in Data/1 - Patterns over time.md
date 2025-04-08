When data includes dates or time values, we'll want to examine whether there might be patterns over time. To illustrate, we'll be working with a subset of a dataset about divorce filings taking place in Mexico from 2000 until 2015. This data contains columns for marriage date and marriage duration in years.
## Importing DateTime data
Before we can begin to look at potential patterns over time, we need to help pandas understand that data in a given column is in fact date or time data. When a CSV file is imported into pandas, date and time data are typically interpreted as strings, as we see here. We can fix that by adding the parse_dates keyword argument to the CSV import and setting it equal to a list of column names that should be interpreted as DateTime data. 
```Python
divorce = pd.read_csv("divorce.csv", parse_dates=["marriage_date"])
marriage.dtypes
>>marriage_date       datetime64[ns]
>>marriage_duration          float64
>>dtype: object
```
Now, when we check the data types of the imported CSV, the indicated column is a DateTime object. This data type opens up many possibilities for analysis, such as looking at patterns over years, months, or even days of the week.
## Converting to DateTime data
Of course, we may wish to update data types to DateTime data after we import the data. This is possible with `pd.to_datetime()`, which converts the argument passed to it to DateTime data. Here, we pass the marriage_date column with values stored as strings to pd.to_datetime. This returns DateTime data which we save as the new marriage_date column.
```Python
divorce["marriage_date"] = pd.to_datetime(marriage["marriage_date"])
divorce.dtypes
>>marriage_date       datetime64[ns]
>>marriage_duration          float64
>>dtype: object
```
## Creating DateTime data
pd.to_datetime has lots of other useful functionality. For example, if a DataFrame has month, day, and year data stored in three different columns, as this one does, we can combine these columns into a single DateTime value by passing them to pd.to_datetime. Note that for this trick to work, columns must be named "month", "day", and "year", but can appear in any order in the DataFrame.
```Python
divorce["marriage_date"] = pd.to_datetime(divorce[["month", "day",
												   "year"]])
```

Conversely, we might want to extract just the month, day, or year from a column containing a full date. If data is already stored in DateTime format, as marriage_date is, we can append `.dt.month` to extract the month attribute, for example. We'll save the month data as a new column in the DataFrame so that we can use it in our analysis.
```Python
divorce["marriage_month"] = divorce["marriage_date"].dt.month
```
## Visualising patterns over time
Line plots are a great way to examine relationships between variables. In Seaborn, line plots aggregate y values at each value of x and show the estimated mean and a confidence interval for that estimate. Perhaps we'd like to check whether there is any relationship between the month that a now-divorced couple got married and the length of their marriage. We can set x equal to the marriage_month column and y equal to marriage_duration. 
```Python
sns.lineplot(data=divorce, x="marriage_month", y="marriage_duration")
plt.show()
```
The results show some variation in mean marriage duration between months. The blue line represents the mean marriage duration for our dataset, while the confidence intervals in the lighter blue shading indicate the area that, with 95% probability, the population mean duration could fall between. The wide confidence intervals suggest that further analysis is needed!
## Let's practice!
It's your turn to practice working with DateTime data with a larger divorce dataset.