- Print the relative frequency of the `"Job_Category"` column from `salaries` DataFrame.
```Python
# Print the relative frequency of Job_Category
print(salaries["Job_Category"].value_counts(normalize=True))
```
