- Read the csv file located at `csv_filepath` into a DataFrame named `df`.
- Print the head of `df` to show the first five rows.
```Python
# Import pandas
import pandas as pd

# Create a DataFrame from csv file
df = pd.read_csv(csv_filepath)

# Print the head of df
print(df.head())
```
View the first five rows of the DataFrame `df`. Is it tidy? Why or why not?
- No, because a single column contains different types of information.