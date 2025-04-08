- Add a column to `planes` containing the standard deviation of `"Price"` based on `"Airline"`.
```Python
# Price standard deviation by Airline
planes["airline_price_st_dev"] = planes.groupby("Airline") \["Price"].transform(lambda x: x.std())

print(planes[["Airline", "airline_price_st_dev"]].value_counts())
```
- Calculate the median for `"Duration"` by `"Airline"`, storing it as a column called `"airline_median_duration"`.
```Python
# Median Duration by Airline
planes["airline_median_duration"] = planes.groupby("Airline") \["Duration"].transform(lambda x: x.median())

print(planes[["Airline","airline_median_duration"]].value_counts())
```
- Find the mean `"Price"` by `"Destination"`, saving it as a column called `"price_destination_mean"`.
```Python
# Mean Price by Destination
planes["price_destination_mean"] = planes.groupby("Destination") \["Price"].transform(lambda x: x.mean())

print(planes[["Destination","price_destination_mean"]].value_counts())
```
