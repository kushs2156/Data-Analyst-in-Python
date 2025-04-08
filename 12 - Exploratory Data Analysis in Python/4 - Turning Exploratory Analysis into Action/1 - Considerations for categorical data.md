Let's see how we convert exploratory data analysis into action! We'll start by looking at class frequencies.
## Why perform EDA?
Recall that EDA is performed for a variety of reasons, like detecting patterns and relationships in data, generating questions or hypotheses, or to prepare data for machine learning models.
## Representative data
There's one requirement our data must satisfy regardless of our plans after performing EDA - it must be representative of the population we wish to study. For example, if we collect data with the aim of analysing the relationship between education level and income in the USA, then we would need to collect this data from adults residing in the USA, and can't rely on data from residents of France.
## Categorical classes
With categorical data, one of the most important considerations is about the representation of classes, which is another term for labels. For example, say we collect data on people's attitudes to marriage. As part of our data collection we find out their marital status, with the classes including single, married, and divorced. When we perform EDA we realise only 50 people were married, while 700 were divorced and the remaining 250 were single. Do we think that this sample accurately represents the general public's opinion about marriage? Are divorced people more likely to have a negative view towards marriage? This is an example of **class imbalance**, where one class occurs more frequently than others. This can bias results, particularly if this class does not occur more frequently in the population.
## Class frequency
We've been counting the number of observations per class using pandas `.value_counts()`, like here:
```Python
print(planes["Destination"].value_counts())
```
where we see how many flights went to different destinations in our planes dataset. Say that we know 40% of internal Indian flights go to Delhi. We can use value_counts method again, but this time set the normalize keyword argument equal to True. 
```Python
print(planes["Destination"].value_counts(normalize=True))
```
This returns the relative frequencies for each class, showing that Delhi only represents 11.8% of destinations in our dataset. Again, this could suggest that our data is not representative of the population - in this case, internal flights in India.
## Cross-tabulation
Another method for looking at class frequency is cross-tabulation, which enables us to examine the frequency of combinations of classes. Let's look at flight route frequencies. We'll start by calling `pd.crosstab()` function. Next we select the column to use as the index for the table, in this case the Source. Lastly, we pass the Destination. Values in this column will become the names of the columns in the table, and the values will be the count of combined observations.
```Python
pd.crosstab(planes["Source"], planes["Destination"])
```
We see the most popular route is from Delhi to Cochin, making up 4318 flights.
## Aggregated values with `pd.crosstab()`
Say we know the median price for all internal flight routes in India. Here they are for the routes in our dataset, measured in Indian Rupees. We can calculate the median price for these routes in our DataFrame, and compare the difference to these expected values. We do this by adding two keyword arguments to pd.crosstab(). We pass the Price column to the values argument, and use aggfunc to select what aggregated calculation we want to perform. We can pass a summary statistic as a string, in this case setting it equal to median. 
```Python
pd.crosstab(planes["Source"], planes["Destination"],
			values=planes["Price"], aggfunc="median")
```
The results show median values for all possible routes in the dataset.

Comparing our prices with the expected values, most are similar. However, routes from Bangalore to Delhi and New Delhi are more expensive in our dataset, suggesting they aren't representative of the population.
## Let's practice!
Now it's your turn to look at class frequencies!