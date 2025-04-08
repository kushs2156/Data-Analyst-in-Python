- Group `planes` by airline and calculate the median price.
- Convert the grouped median prices to a dictionary.
- Conditionally impute missing values for `"Price"` by mapping values in the `"Airline"` column based on `prices_dict`.
- Check for remaining missing values.
```Python
# Calculate median plane ticket prices by Airline
airline_prices = planes.groupby("Airline")["Price"].median()

print(airline_prices)

# Convert to a dictionary
prices_dict = planes.groupby("Airline")["Price"].median().to_dict()

# Map the dictionary to missing values of Price by Airline
planes["Price"] = planes["Price"].fillna(planes["Airline"]
									.map(prices_dict))

# Check for missing values
print(planes.isna().sum())
```


