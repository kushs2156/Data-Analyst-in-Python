- Create a column called `mean_rate_2021` which shows the mean 2021 unemployment rate for each continent.
- Create a column called `std_rate_2021` which shows the standard deviation of the 2021 unemployment rate for each continent.
```Python
continent_summary = unemployment.groupby("continent").agg(
    # Create the mean_rate_2021 column
    mean_rate_2021=("2021", "mean"),
    # Create the std_rate_2021 column
    std_rate_2021=("2021", "std")
)
print(continent_summary)
```