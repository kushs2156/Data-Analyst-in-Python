Write a `for` loop that iterates over the rows of `cars` and on each iteration perform two `print()` calls: one to print out the row label and one to print out all of the rows contents.
```Python
# Import cars data
import pandas as pd
cars = pd.read_csv('cars.csv', index_col = 0)

# Iterate over rows of cars
for row, label in cars.iterrows():
    print(row)
    print(label)
```
