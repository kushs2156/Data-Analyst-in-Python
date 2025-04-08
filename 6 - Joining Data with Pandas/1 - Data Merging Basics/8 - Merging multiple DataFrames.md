Welcome back. In our last lesson, we learned how to merge two tables with a one-to-many relationship using the merge method. Merging data like this is a necessary skill to bring together data from different sources to answer some more complex data questions. Sometimes we need to merge together more than just two tables to complete our analysis.

In the previous lesson, we used two tables from the city of Chicago. One table contained business licenses issued by the city. The other table listed info about the local neighbourhoods called wards, including the local government official's office. Now, we also have a table of businesses that have received small business grant money from Chicago. The grants are funded by taxpayer money. Therefore, it would be helpful to analyse how much grant money each business received and in what ward that business is located. We then could determine if one ward's businesses received a disproportionately large amount of grant money.
## Tables to merge
To pull all of this information together, let's first connect our grants table to our licenses table. The two tables are related by their company name and location. Let's pause here for a moment. If we merge the two tables only using the zip column, then the 60616 zip of Reggie's bar from the licenses table will be matched to multiple businesses in the grants table with the same zip. Our code sample prints the first few rows and some columns of the merged table. The output of the merge duplicates Reggie's bar for each matching zip in the grants table, which is not what we want. If instead, we merged on address only, there's a small risk that the address would repeat in different parts of the city. Therefore, the best option is to merge the tables using the combination of both address and zip code.
## Single merge
We merge the two DataFrames as shown before, except in this case, we pass a list of the column names we want to merge on to the 'on' argument. This allows us to use multiple columns in the merge. 
```Python
grants.merge(licenses, on=['address', 'zip'])
```
As before, the matching rows between the two DataFrames are returned with the columns from the grant table listed first. However, when we merge on two columns, in this case address and zip code, we are requiring that both the address and zip code of a row in the left table match the address and zip code of a row in the right table in order for them to be linked to each other in the merge.
## Merging multiple tables
We can now extend this example to a third table. First, we merge the grants table with the wards table on the ward column again, adding suffixes to the repeated column names. Note that we're using Python's backslash line continuation method to add the second merge on the next line. Python will read this as just one line of code. Without this, Python will throw a syntax error since it will parse it as two separate lines of code, so don't forget your backslash. 
```Python
grants_licenses_ward = grants.merge(licenses, on=['address', 'zip']) \
							.merge(wards, on='ward', suffixes=('_bus',                             '_ward'))
grants_licenes_ward.head()
```
Now our output table has information about grants, business, and wards. We can now complete our analysis. We can now sum the grants by ward and plot the results. Some wards have received more grants than others.
```Python
import matplotlib.pyplot as plt
grants_licenses_ward.groupby('ward').agg('sum').plot(kind='bar', 
													 y='grant')
plt.show()
```
## Merging even more...
We could continue to merge additional tables as needed. We stopped at three, but if needed, we could continue to add more. The code here shows the pattern you would follow as you merge more tables.
```Python
# Three tables
df1.merge(df2, on='col') \
   .merge(df3, on='col')

# Four tables
df1.merge(df2, on='col') \
   .merge(df3, on='col') \
   .merge(df4, om='col')
```
## Let's practice
Now, let's practice merging multiple tables.