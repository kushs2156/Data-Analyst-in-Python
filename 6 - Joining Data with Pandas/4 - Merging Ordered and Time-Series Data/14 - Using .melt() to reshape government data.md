- Use `.melt()` to unpivot all of the columns of `ur_wide` except `year` and ensure that the columns with the months and values are named `month` and `unempl_rate`, respectively. Save the result as `ur_tall`.
- Add a column to `ur_tall` named `date` which combines the `year` and `month` columns as _year_-_month_ format into a larger string, and converts it to a date data type.
- Sort `ur_tall` by date and save as `ur_sorted`.
- Using `ur_sorted`, plot `unempl_rate` on the y-axis and `date` on the x-axis.
```Python
# unpivot everything besides the year column
ur_tall = ur_wide.melt(id_vars='year', var_name='month', 
						value_name='unempl_rate')

# Create a date column using the month and year columns of ur_tall
ur_tall['date'] = pd.to_datetime(ur_tall['year'] + ' ' +                                                 ur_tall['month'])

# Sort ur_tall by date in ascending order
ur_sorted = ur_tall.sort_values('date')

# Plot the unempl_rate by date
ur_sorted.plot(x='date', y='unempl_rate')
plt.show()
```
![[download 31.svg]]
