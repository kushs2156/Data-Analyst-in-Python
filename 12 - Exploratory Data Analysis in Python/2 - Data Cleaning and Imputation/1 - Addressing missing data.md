Hi, I'm George, and in this video we'll look at strategies for handling missing data.
## Why is missing data a problem?
So, why is it important to deal with missing data? Well, it can affect distributions. As an example, we collect the heights of students at a high school. If we fail to collect the heights of the oldest students, who were taller than most of our sample, then our sample mean will be lower than the population mean. Put another way, our data is less representative of the underlying population. In this case, parts of our population aren't proportionately represented. This misrepresentation can lead us to draw incorrect conclusions, like thinking that, on average, students are shorter than they really are.
## Data professionals' job data
Let's illustrate how missing data impacts exploratory analysis using a dataset about data professionals. This dataset includes the year the data was obtained, job title, experience level, type of employment, location, company size, time spent working remotely, and salary in US dollars. To highlight the impact of missing values, let's look at salaries by experience level using a full version of the dataset. Now, let's compare this to the same data with some missing values. The y-axis shows that the largest salary is around 150000 dollars less in the second plot!
## Checking for missing values
With our dataset stored as a pandas DataFrame called salaries, we can count the number of missing values per column by chaining the `.isna()` and `.sum()` methods. isna refers to the fact that missing values are represented as na in DataFrames. 
```Python
print(salaries.isna().sum())
```
The output shows all columns contain missing values, with Salary_USD missing 60 values.
## Strategies for addressing missing data
There are various approaches to handle missing data. One rule of thumb is to ==remove observations== if they amount to ==five percent or less of all values==. If we have more missing values, instead of dropping them, we can replace them with a summary statistic like the mean, median, or mode, depending on the context. This is known as **imputation**. Alternatively, we can impute by sub-groups. We saw that median salary varies by experience, so we could impute different salaries depending on experience.
## Dropping missing values
To calculate our missing values threshold we multiply the length of our DataFrame by five percent, giving us an upper limit of 30.
```Python
threshold = len(salaries) *0.05
print(threshold)
>>30
```
We can use Boolean indexing to filter for columns with missing values less than or equal to this threshold, storing them as a variable called cols_to_drop. Printing cols_to_drop shows four columns. 
```Python
cols_to_drop = salaries.columns[salaries.isna().sum() <= threshold]
```
We drop missing values by calling `.dropna()`, passing cols_to_drop to the subset argument. We set inplace to True so the DataFrame is updated.
```Python
salaries.dropna(subset=cols_to_drop, inplace=True)
```
## Imputing a summary statistic
We then filter for the remaining columns with missing values, giving us four columns. To impute the mode for the first three columns, we loop through them and call the `.fillna()` method, passing the respective column's mode and indexing the first item, which contains the mode, in square brackets.
```Python
cols_with_missing_values = salaries.columns[salaries.isna().sum() > 0]

for col in cols_with_missing_values[:-1]:
	salaries[col].fillna(salaries[col].mode()[0])
```
## Checking the remaining missing values
Checking for missing values again, we see salary_USD is now the only column with missing values and the volume has changed from 60 missing values to 41. This is because some rows may have contained missing values for our subset columns as well as salary, so they were dropped.
## Imputing by sub-group
We'll impute median salary by experience level by grouping salaries by experience and calculating the median. We use the `.to_dict()` method, storing the grouped data as a dictionary. Printing the dictionary returns the median salary for each experience level, with executives earning the big bucks!
```Python
salaries_dict = salaries.groupby("Experience")["Salary_USD"].median().to_dict()
print(salaries_dict)
>>{'Entry': 55380.0, 'Executive': 135439.0, 'Mid': 74173.5, 
	'Senior': 128903.0}
```
We then impute using the .fillna() method, providing the Experience column and calling the `.map()` method, inside which we pass the salaries dictionary.
```Python
salaries["Salary_USD"] = salaries["Salary_USD"].fillna(salaries["Experience"].map
										(salaries_dict))
```
Now we see there are no more missing values!
## Let's practice!
Let's practice working with missing data!