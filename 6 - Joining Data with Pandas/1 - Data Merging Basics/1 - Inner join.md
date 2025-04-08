Welcome! I am Aaren Stubberfield and I will be your instructor for this course. The pandas package is a powerful tool for manipulating and transforming data in Python. However, when working on an analysis, the data needed could be in multiple tables. This course will focus on the vital skill of merging tables together.
## For clarity
As we start, two quick clarifications. First, through other courses on DataCamp, you may have learned how to import tabular data as DataFrames. In this course, you may hear the words table and DataFrame, but they are equivalent here. Second, we will refer to combining different tables together as merging tables, but note that some refer to this same process as joining. To help us learn about merging tables, we will use data from the city of Chicago data portal.
## Datasets for example
The city of Chicago is divided into fifty local neighbourhoods called wards. We have a table with data about the local government offices in each ward. In this example, we want to merge the local government data with census data about the population of each ward. If we look at the wards table, we have information about the local government of each ward, such as the government office address. This table has 50 rows and 4 columns, or one row for each ward. The census table contains the population of each ward in 2000 and 2010, and that change as a percentage. Additionally, it includes the address for the centre of each ward. This table has 50 rows and 6 columns.
## Merging tables
The two tables are related by their ward column. We can merge them together, matching the ward number from each row of the wards table to the ward numbers from the census table. For example, the second ward in the wards table with Alderman Brian Hopkins would be matched with row 2 of the census table where the population in 2000 was 54,361.
## Inner Join
The pandas package has an excellent DataFrame method for performing this type of merge called merge. The `.merge()` method takes the first DataFrame, wards, and merges it with the second DataFrame, census. We use the **on** argument to tell the method that we want to merge the two DataFrames on the ward column. 
```Python
wards_census = wards.merge(census, on='ward')

print(wards_census.shape)
>>(50, 9)
```
Since we listed the wards table first, its columns will appear first in the output, followed by the columns from the census table. In this example, the merge returns a DataFrame with 50 rows and 9 columns, where the returned rows have matching values for the ward column in both tables. This is called an inner join.

An inner join will only return rows that have matching values in both tables.
## Suffixes
You may have noticed that the merged table has columns with suffixes of underscore x or y. This is because both the wards and census tables contained address and zip columns. To avoid multiple columns with the same name, they are automatically given a suffix by the merge method.
```Python
print(wards_census.columns)
>>Index(['ward', 'alderman', 'address_x', 'zip_x', 'pop_2000', 'pop_2010', 'change', 'address_y', 'zip_y'], dtype='object')
```
We can use the suffix argument of the merge method to control this behaviour. We provide a tuple where all of the overlapping columns in the left table are given the suffix 'ward', and those of the right table will be given the suffix 'cen'. This makes it easier for us to tell the difference between the columns.
```Python
wards_census = ward.merge(census, on='ward', suffixes=('_ward', '_cen'))
```
## Let's practice!
Now let's practice using the merge method.