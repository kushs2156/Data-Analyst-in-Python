- Find the 75th and 25th percentiles, saving as `price_seventy_fifth` and `price_twenty_fifth` respectively.
- Calculate the IQR, storing it as `prices_iqr`.
- Calculate the upper and lower outlier thresholds.
- Remove the outliers from `planes`.
```Python
# Find the 75th and 25th percentiles
price_seventy_fifth = planes["Price"].quantile(0.75)
price_twenty_fifth = planes["Price"].quantile(0.25)

# Calculate iqr
prices_iqr = price_seventy_fifth - price_twenty_fifth

# Calculate the thresholds
upper = price_seventy_fifth + (prices_iqr * 1.5)
lower = price_twenty_fifth - (prices_iqr * 1.5)

# Subset the data
planes = planes[(planes["Price"] > lower) & (planes["Price"] < upper)]

print(planes["Price"].describe())
```
