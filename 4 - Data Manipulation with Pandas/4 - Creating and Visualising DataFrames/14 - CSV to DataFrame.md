- Read the CSV file `"airline_bumping.csv"` and store it as a DataFrame called `airline_bumping`.
- Print the first few rows of `airline_bumping`.
- For each airline group, select the `nb_bumped`, and `total_passengers` columns, and calculate the sum (for both years). Store this as `airline_totals`.
- Create a new column of `airline_totals` called `bumps_per_10k`, which is the number of passengers bumped per 10,000 passengers in 2016 and 2017.
- Print `airline_totals` to see the results of your manipulations.

```Python
# Read CSV as DataFrame called airline_bumping
airline_bumping = pd.read_csv("airline_bumping.csv")

# Take a look at the DataFrame
print(airline_bumping.head())

# For each airline, select nb_bumped and total_passengers and sum
airline_totals = airline_bumping.groupby("airline")[["nb_bumped", "total_passengers"]].sum()

# Create new col, bumps_per_10k: no. of bumps per 10k passengers for each airline
airline_totals["bumps_per_10k"] = airline_totals["nb_bumped"] / airline_totals["total_passengers"] * 10000

# Print airline_totals
print(airline_totals)
```