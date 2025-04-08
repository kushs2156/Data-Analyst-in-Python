- Import `numpy` with the alias `np`.
- Subset `food_consumption` to get the rows where the `country` is `'USA'`.
- Calculate the mean of food `consumption` in the `usa_consumption` DataFrame, which is already created for you.
- Calculate the median of food `consumption` in the `usa_consumption` DataFrame.
```Python
# Import numpy with alias np
import numpy as np

# Subset country for USA: usa_consumption
usa_consumption = food_consumption[food_consumption['country'] 
										== 'USA']

# Calculate mean consumption in USA
print(np.mean(usa_consumption['consumption']))

# Calculate median consumption in USA
print(np.median(usa_consumption['consumption']))
```
