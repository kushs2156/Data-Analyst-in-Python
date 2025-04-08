Sometimes the format of our data can limit our ability to detect relationships or inhibit the potential performance of machine learning models. One method to overcome these issues is to generate new features from our data!
## Correlation and viewing data types
Checking correlation with a heatmap, we see a moderate positive correlation between Price and Duration, but it looks like those are the only numeric variables in our dataset.
```Python
sns.heatmap(planes.corr(), annot=True)
plt.show()
```

Viewing the data types confirms this is the case. However, Total_Stops should also be numeric. Viewing the value_counts, we see we need to remove string characters, and change non-stop to zero, before converting the data type to integer. We use the str.replace method to first remove " stops", including the space, so that flights with two, three, or four stops are ready to convert. 
```Python
planes["Total_Stops"] = planes["Total_Stops"].str.replace(" stops", "")
planes["Total_Stops"] = planes["Total_Stops"].str.replace(" stop", "")
planes["Total_Stops"] = planes["Total_Stops"].str.replace \ 
							("non-stop", 0)
planes["Total_Steps"] = planes["Total_Stops"].astype(int)
```
Next we clean flights with one stop. Lastly, we change "non-stop" to "0", then set the data type to integer.
```Python
sns.heatmap(planes.corr(), annot=True)
plt.show()
```
Unsurprisingly, Total_Stops is strongly correlated with Duration. What is interesting is that Total_Stops and Price are more strongly correlated than Duration is with Price! Let's see what else we can find out!
## Dates
Rechecking our data types, notice that there are three datetime variables - Date_of_Journey, Dep_Time, and Arrival_Time. We know how to extract attributes from datetime values, so we can see if these offer any insights into pricing. To start, let's look at Date_of_Journey. If we think prices vary per month, it's worth using this attribute - we create it as a column in our DataFrame. Perhaps prices might also differ depending on the day of the week? Let's grab that using the `dt.weekday` attribute. It returns values of zero, representing Monday, through to six, for Sunday. Previewing these columns we see the first flight, departing on the 6th September, was a Friday, indicated by a four.
```Python
planes["month"] = planes["Date_of_Journey"].dt.month
planes["weekday"] = planes["Date_of_Journey"].dt.weekday
print(planes[["month", "weekday", "Date_of_Journey"]].head())
```
## Departure and arrival times
We might wonder if people tend to pay more to depart or arrive at more convenient times. We extract the hour of departure and arrival from those respective columns too.
```Python
planes["Dep_Hour"] = planes["Dep_Time"].dt.hour
planes["Arrival_Hour"] = planes["Arrival_Time"].dt.hour
```
Because they are numeric, we can calculate correlation between these new datetime features and other variables. Re-plotting our heatmap, unfortunately there aren't any new strong relationships. But we wouldn't have known this if we hadn't generated these features.
## Creating categories
There's one more technique we can use to generate new features. We can group numeric data and label them as classes. For example, we don't have a column for ticket type. We could use descriptive statistics to label flights as economy, premium economy, business class, or first class, based on prices within specific ranges, or bins.

We'll split equally across the price range using quartiles. We first store the 25th percentile using the quantile method. We get the 50th percentile by calling the median. Next we get the 75th percentile, and lastly, we store the maximum value.
```Python
twenty_fifth = planes["Price"].quantile(0.25)
median = planes["Price"].median()
seventy_fifth = planes["Price"].quantile(0.75)
maximum = planes["Price"].max()
```
We create the labels, in this case our ticket types, and store as a list. Next, we create the bins, a list starting from zero and including our descriptive statistic variables.
```Python
labels = ["Economy", "Premium Economy", "Business Class", 
		  "First Class"]
bins = [0, twenty_fifth, median, seventy_fifth, maximum]
```
We now call the `pd.cut()` function, passing our Price column, setting the labels argument equal to our labels variable, and the bins argument equal to our bins.
```Python
planes["Price_Category"] = pd.cut(planes["Price"],
								  labels=labels,
								  bins=bins)
```
Previewing the Price and Price_Category columns, we see the mapping has been successfully applied! We can plot the count of flights in different categories per airline by passing our new column to the hue argument when calling sns.countplot.
```Python
sns.countplot(data=planes, x="Airline", hue="Price_Category")
plt.show()
```
Looks like Jet Airways has the largest number of "First Class" tickets, while most of IndiGo and SpiceJet's flights are "Economy".
## Let's practice!
Let's generate some new features in our data professionals dataset!