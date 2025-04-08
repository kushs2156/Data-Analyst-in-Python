Let's look at how to handle outliers.
## What is an outlier?
To recap, an outlier is an observation that is far away from other data points. If a house prices dataset has a median of 400,000 dollars, a house that costs five million dollars would likely be considered an outlier. However, we should consider factors that affect price such as location, number of bedrooms, and overall size.
## Using descriptive statistics
A starting place for identifying outliers is with the pandas .describe method. 
```Python
print(salaries["Salary_USD"].describe())
```
We can see that the maximum salary is more than four times the mean and median. Seems extreme right?
## Using the Interquartile range
We can define an outlier mathematically. First, we need to know the interquartile range, or IQR, which is the difference between the 75th and 25th percentiles.
```Python
sns.boxplot(data=salaries, x="Salary_USD")
plt.show()
```
Recall that these percentiles are included in box plots, like this one showing salaries of data professionals. The box contains percentiles, and observations considered to be outliers are represented as diamonds outside of the box.

Once we have the IQR, we can find an upper outlier by looking for values above the sum of the 75th percentile plus 1.5 times the IQR. Lower outliers have values below the sum of the 25th percentile minus 1.5 times the IQR. We can calculate percentiles using the `Series.quantile()` method. We pass 0.75 to find the 75th percentile for salary, then pass 0.25 to get the 25th percentile. We calculate the IQR by subtracting one from the other. Printing the result shows an IQR of around 76000 dollars.
```Python
# 75th percentile
seventy_fifth = salaries["Salary_USD"].quantile(0.75)

# 25th percentile
twenty_fifth = salaries["Salary_USD"].quantile(0.25)

salaries_iqr = seventy_fifth - twenty_fifth

print(salaries_iqr)
>>76305.0
```

We can plug these variables into our formulae to find the value thresholds, first for the upper limit and then for the lower limit. Printing the results, we can see that the lower limit is actually below zero, which isn't possible given we are working with salaries!
```Python
# Upper threshold
upper = seventy_fifth + (1.5 * salaries_iqr)

# Lower threshold
lower = twenty_fifth - (1.5 * salaries_iqr)

print(upper, lower)
251953.5 -53266.5
```
## Subsetting our data
We can find values outside of these limits by subsetting our data. It will only return upper outliers, but for the purpose of demonstrating the syntax, we've also filtered for values below the lower threshold. We also subset to just show Experience, Employee_Location, and Salary_USD. 
```Python
salaries[(salaries["Salary_USD"] < lower) | \
	salaries["Salary_USD"] > upper] \
		[["Experience", "Employee_Location", "Salary_USD"]]
```
There are nine individuals with a salary above the upper threshold. Notice how none of them are entry level and they are all based in the US?
## Why look for outliers?
So why is the detection of outliers an important part of exploratory data analysis? These are extreme values and may not accurately represent the data. Additionally, they can skew the mean and standard deviation. If we plan to perform statistical tests or build machine learning models, these will often require data that is normally distributed and not skewed!
## What to do about outliers?
Once we know we have outliers, we need to decide what to do. It's helpful to ask ourselves why these outliers exist. For example, salaries can be very high depending on level of experience and the country of employment, so could be representative of a subset of our data. If this is the case, we could just leave them alone. Alternatively, do we know the values are accurate? Could there have been an error in data collection? If there's an error, we could remove the values.
## Dropping outliers
We can remove outliers by modifying the syntax we used to subset our data, filtering for values more than the lower limit and less than the upper limit.
```Python
no_outliers = salaries[(salaries["Salary_USD"] > lower) & \ 
					   (salaries["Salary_USD"] < upper)]
```
Reprinting our descriptive statistics shows nine fewer values, a mean that is 5000 dollars less than before, and a much lower maximum salary!
## Distribution of salaries
To highlight the impact of removing outliers, let's plot a histogram of the original dataset containing the outliers. We see the distribution is right-skewed by the upper outliers. Plotting with the no_outliers dataset, salaries is now less skewed and looks more like a normal distribution!
## Let's practice!
Time for you to practice working with outliers!