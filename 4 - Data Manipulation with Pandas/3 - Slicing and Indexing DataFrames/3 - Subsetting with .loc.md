- Create a list called `cities` that contains "Moscow" and "Saint Petersburg".
- Use `[]` subsetting to filter `temperatures` for rows where the `city` column takes a value in the `cities` list.
- Use `.loc[]` subsetting to filter `temperatures_ind` for rows where the city is in the `cities` list.
```Python
# Make a list of cities to subset on
cities = ["Moscow", "Saint Petersburg"]

# Subset temperatures using square brackets
print(temperatures[temperatures["city"].isin(cities)])

# Subset temperatures_ind using .loc[]
print(temperatures_ind.loc[cities])
```
