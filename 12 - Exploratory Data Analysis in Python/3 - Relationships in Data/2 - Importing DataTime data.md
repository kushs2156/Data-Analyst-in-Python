- Import `divorce.csv`, saving as a DataFrame, `divorce`; indicate in the import function that the `divorce_date`, `dob_man`, `dob_woman`, and `marriage_date` columns should be imported as DateTime values.
```Python
# Import divorce.csv, parsing the appropriate columns as dates in the import
divorce = pd.read_csv("divorce.csv", parse_dates =
		["divorce_date", "dob_man", "dob_woman", "marriage_date"])
print(divorce.dtypes)
```
