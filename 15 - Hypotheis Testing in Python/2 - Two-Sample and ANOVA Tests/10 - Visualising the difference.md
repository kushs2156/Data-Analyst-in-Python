- Create a new `diff` column containing the percentage of votes for the democratic candidate in 2012 minus the percentage of votes for the democratic candidate in 2016.
- Calculate the mean of the `diff` column as `xbar_diff`.
- Calculate the standard deviation of the `diff` column as `s_diff`.
- Plot a histogram of the `diff` column with 20 bins.
```Python
# Calculate the differences from 2012 to 2016
sample_dem_data['diff'] = sample_dem_data['dem_percent_12'] - 
						  sample_dem_data['dem_percent_16']

# Print sample_dem_data
print(sample_dem_data)

# Find the mean of the diff column
xbar_diff = sample_dem_data['diff'].mean()

# Print xbar_diff
print(xbar_diff)
>>6.829312660106834

# Find the standard deviation of the diff column
s_diff = sample_dem_data['diff'].std()

# Print s_diff
print(s_diff)
>>5.040139140132317

# Plot a histogram of diff with 20 bins
sample_dem_data['diff'].hist(bins=20)
plt.show()
```
![[download 131.svg]]
