You could be given a DataFrame that has missing values, so it's important to know how to handle them. Most data is not perfect - there's always a possibility that there are some pieces missing from your dataset. For example, maybe on the day that Bella and Cooper's owner weighed them, the scale was broken. Now we have two missing values in our dataset.

In a pandas DataFrame, missing values are indicated with `NaN`, which stands for "not a number". When you first get a DataFrame, it's a good idea to get a sense of whether it contains any missing values, and if so, how many. That's where the `.isna()` method comes in. When we call `.isna()` on a DataFrame, we get a Boolean for every single value indicating whether the value is missing or not, but this isn't very helpful when you're working with a lot of data. If we chain .isna() with `.any()`, we get one value for each variable that tells us if there are any missing values in that column. Here, we see that there's at least one missing value in the weight column, but not in any of the others.
```Python
dogs.isna()

dogs.isna().any()

dogs.isna().sum()
```
Since taking the sum of Booleans is the same thing as counting the number of Trues, we can combine sum with isna() to count the number of NaNs in each column.
## Plotting missing values
We can use those counts to visualise the missing values in the dataset using a bar plot. Plots like this are more interesting when you have missing data across different variables, while here, only weights are missing. 
```Python
import matplotlib.pyplot as plt
dogs.isna().sum().plot(kind="bar")
plt.show()
```
Now that we know there are missing values in the dataset, what can we do about them?
## Removing missing values
One option is to remove the rows in the DataFrame that contain missing values. This can be done using the `.dropna()` method. However, this may not be ideal if you have a lot of missing data, since that means losing a lot of observations.
```Python
dogs.dropna()
```
## Replacing missing values
Another option is to replace missing values with another value. The `.fillna()` method takes in a value, and all NaNs will be replaced with this value. There are also many sophisticated techniques for replacing missing values, which you can learn more about in our course about missing data.
```Python
dogs.fillna(0)
```
## Let's practice
Alright, time to wrangle with some missing values on your own!