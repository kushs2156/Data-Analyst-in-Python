- Set the index of `temperatures` to the `"country"` and `"city"` columns, and assign this to `temperatures_ind`.
- Specify two country/city pairs to keep: `"Brazil"`/`"Rio De Janeiro"` and `"Pakistan"`/`"Lahore"`, assigning to `rows_to_keep`.
- Print and subset `temperatures_ind` for `rows_to_keep` using `.loc[]`.
```Python
# Index temperatures by country & city
temperatures_ind = temperatures.set_index(["country", "city"])

# List of tuples: Brazil, Rio De Janeiro & Pakistan, Lahore
rows_to_keep = [("Brazil", "Rio De Janeiro"), ("Pakistan", "Lahore")]

# Subset for rows to keep
print(temperatures_ind.loc[rows_to_keep])
```
