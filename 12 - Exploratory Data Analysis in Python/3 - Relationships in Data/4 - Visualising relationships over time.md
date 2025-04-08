- Define a column called `marriage_year`, which contains just the year portion of the `marriage_date` column.
- Create a line plot showing the average number of kids a couple had during their marriage, arranged by the year that the couple got married.
```Python
# Define the marriage_year column
divorce["marriage_year"] = divorce["marriage_date"].dt.year

# Define the marriage_year column
divorce["marriage_year"] = divorce["marriage_date"].dt.year

# Create a line plot showing the average number of kids by year
sns.lineplot(data=divorce, x="marriage_year", y="num_kids")
plt.show()
```
![[download 107.svg]]
