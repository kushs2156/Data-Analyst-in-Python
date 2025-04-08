- Use `merge_ordered()` to merge `gdp` and `sp500` using a left join where the `year` column from `gdp` is matched with the `date` column from `sp500`.
- Print `gdp_sp500`.
```Python
# Use merge_ordered() to merge gdp and sp500 on year and date
gdp_sp500 = pd.merge_ordered(gdp, sp500, left_on='year', 
							 right_on='date', how='left') 

# Print gdp_sp500
print(gdp_sp500)
```
- Use the `merge_ordered()` function again, similar to before, to merge `gdp` and `sp500`, using the function's ability to fill in missing data for returns by forward-filling the missing values. Assign the resulting table to the variable `gdp_sp500`.
```Python
# Use merge_ordered() to merge gdp and sp500, and forward fill missing values
gdp_sp500 = pd.merge_ordered(gdp, sp500, left_on='year', 
					right_on='date', how='left', fill_method='ffill')

# Print gdp_sp500
print (gdp_sp500)
```
- Subset the `gdp_sp500` table, select the `gdp` and `returns` columns, and save as `gdp_returns`.
- Print the correlation matrix of the `gdp_returns` table using the `.corr()` method.
```Python
# Use merge_ordered() to merge gdp and sp500, and forward fill missing values
gdp_sp500 = pd.merge_ordered(gdp, sp500, left_on='year', 
			right_on='date',how='left',  fill_method='ffill')

# Subset the gdp and returns columns
gdp_returns = gdp_sp500[['gdp', 'returns']]

# Print gdp_returns correlation
print (gdp_returns.corr())
>>            gdp  returns
>>gdp       1.000    0.212
>>returns   0.212    1.000
```
