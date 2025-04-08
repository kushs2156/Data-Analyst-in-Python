- Use `loc` or `iloc` to select the observation corresponding to Japan as a Series. The label of this row is `JPN`, the index is `2`. Make sure to print the resulting Series.
- Use `loc` or `iloc` to select the observations for Australia and Egypt as a DataFrame. You can find out about the labels/indexes of these rows by inspecting `cars`. Make sure to print the resulting DataFrame.
```Python
# Import cars data
import pandas as pd
cars = pd.read_csv('cars.csv', index_col = 0)

# Print out observation for Japan
print(cars.iloc[2])

# Print out observations for Australia and Egypt
print(cars.loc[["AUS", "EG"]])
```
