Time to switch our focus on to working with numeric data.
## The original salaries dataset
So far, we've been looking at a modified version of the data professionals dataset. Let's print summary information about our original DataFrame.
```Python
salaries.info()
```
The first thing that jumps out is that the Salary_USD column we've been working with is not present, but there's a column called Salary_In_Rupees, referring to India's currency. Previewing this column, we see that the values contain commas, and the data type is object.
## Converting strings to numbers
To obtain Salary in USD we'll need to perform a few tasks. First, we need to remove the commas from the values in the Salary_In_Rupees column. Next, we change the data type to float. Lastly, we'll make a new column by converting the currency.

To remove commas, we can use the `pd.Series.str.replace()` method. We first pass the characters we want to remove, followed by the characters to replace them with. As we don't want to add characters back in, when we update the column we provide an empty string in this part of the method. 
```Python
salaries["Salary_In_Rupees"] = 
	salaries["Salary_In_Rupees"].str.replace(",", "")
```
Printing the first five rows of this column, we see the commas have been removed. However, the column is still object data type.
```Python
salaries["Salary_In_Rupees"] = salaries["Salary_In_Rupees"].astype(float)
```
We update the data type to float.
We've looked up the conversation rate from Indian rupees to US dollars, and currently one rupee is worth 0.012 cents. To create the Salary_USD column we multiply the values in the rupees column by 0.012.
```Python
salaries["Salary_USD"] = salaries["Salary_In_Rupees"] * 0.012
```
Printing the first five rows of the original and new column, we can see that values in Salary_USD are equal to 1.2 percent of the Salary_In_Rupees column.
## Adding summary statistics into a DataFrame
Recall that we've previously used pandas' groupby function to calculate summary statistics. Here, we find the mean salary in US dollars by company size. While this is useful, sometimes we might prefer to add summary statistics directly into our DataFrame, rather than creating a summary table.
```Python
salaries.groupby("Company_Size")["Salary_USD"].mean()
```
Let's say we would like to create a new column containing the standard deviation of Salary_USD, where values are conditional based on the Experience column. The first step still involves a groupby, done here with the Experience column. We then select the Salary_USD column, and call pandas `.transform()`. Inside the transform call, we apply a lambda function using the syntax lambda x semi-colon, followed by a call of x.std. This calculates the standard deviation of salaries based on experience.
```Python
salaries["std_dev"] = salaries.groupby("Experience")["Salary_USD"].transform(lambda x: x.std())
```

We can select more than one column and use the value_counts method. This prints the combinations of values for the columns we have chosen, in this case Experience and newly created std_dev columns. 
```Python
print(salaries[["Experience", "std_dev"]].value_counts())
```
For example, there are 257 rows with SE, or Senior-level, experience, and the standard deviation in salary for this group is nearly 53000 dollars. Unsurprisingly, there appears to be a larger variation in salary associated with the most senior role, Executive.

We can repeat this process for other summary statistics! Here, we add a column for the median salary based on company size. We use a backslash to split our code over two lines, otherwise it is quite long and difficult to read. 
```Python
salaries["median_by_comp_size"] = salaries.groupby("Company_Size") \
					["Salary_USD"].transform(lambda x: x.median())
```
Previewing the two columns of interest we see the values have been mapped correctly and that medium-sized companies have the largest median salary!
```Python
print(salaries[["Company_Size", "median_by_comp_size"]].head())
```
## Let's practice!
Now it's your turn to explore some numeric data!