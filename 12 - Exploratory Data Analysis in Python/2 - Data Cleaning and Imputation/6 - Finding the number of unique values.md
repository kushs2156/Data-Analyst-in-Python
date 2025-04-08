- Filter `planes` for columns that are of `"object"` data type.
- Loop through the columns in the dataset.
- Add the column iterator to the print statement, then call the function to return the number of unique values in the column.
```Python
# Filter the DataFrame for object columns
non_numeric = planes.select_dtypes("object")

# Loop through columns
for col in non_numeric.columns:
  # Print the number of unique values
  print(f"Number of unique values in {col} column: ", 
				  non_numeric[col].nunique())
```