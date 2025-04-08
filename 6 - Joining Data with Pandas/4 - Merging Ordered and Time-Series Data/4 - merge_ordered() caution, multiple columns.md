- Use `merge_ordered()` on `gdp` and `pop`, merging on columns `date` and `country` with the fill feature, save to `ctry_date`.
- Perform the same merge of `gdp` and `pop`, but join on `country` and `date` (**reverse of step 1**) with the fill feature, saving this as `date_ctry`.
```Python
# Merge gdp and pop on date and country with fill and notice rows 2 and 3
ctry_date = pd.merge_ordered(gdp, pop, on=['date', 'country'], 
							 fill_method='ffill')

# Print ctry_date
print(ctry_date)

# Merge gdp and pop on country and date with fill
date_ctry = pd.merge_ordered(gdp, pop, on=['country', 'date'], 
							 fill_method='ffill')

# Print date_ctry
print(date_ctry)
```