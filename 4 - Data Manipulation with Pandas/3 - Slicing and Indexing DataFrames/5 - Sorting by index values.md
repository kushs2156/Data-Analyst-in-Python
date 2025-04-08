- Sort `temperatures_ind` by the index values.
- Sort `temperatures_ind` by the index values at the `"city"` level.
- Sort `temperatures_ind` by ascending country then descending city.
```Python
# Sort temperatures_ind by index values
print(temperatures_ind.sort_index())

# Sort temperatures_ind by index values at the city level
print(temperatures_ind.sort_index(level=["city", "country"]))

# Sort temperatures_ind by country then descending city
print(temperatures_ind.sort_index(level=["country", "city"], ascending=[True, False]))
```
