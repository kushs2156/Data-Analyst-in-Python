- Count the number of stores of each store `type` in `store_types`.
- Count the proportion of stores of each store `type` in `store_types`.
- Count the number of stores of each `department` in `store_depts`, sorting the counts in descending order.
- Count the proportion of stores of each `department` in `store_depts`, sorting the proportions in descending order.
```Python
# Count the number of stores of each type
store_counts = store_types["type"].value_counts()
print(store_counts)

# Get the proportion of stores of each type
store_props = store_types["type"].value_counts(normalize=True)
print(store_props)

# Count the number of stores for each department and sort
dept_counts_sorted = store_depts["department"].value_counts(sort=True)
print(dept_counts_sorted)

# Get the proportion of stores in each department and sort
dept_props_sorted = store_depts["department"].value_counts(sort=True, normalize=True)
print(dept_props_sorted)
```
