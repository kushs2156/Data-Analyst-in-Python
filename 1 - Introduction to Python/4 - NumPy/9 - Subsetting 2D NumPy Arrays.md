- Print out the 50th row of `np_baseball`.
- Make a new variable, `np_weight_lb`, containing the entire second column of `np_baseball`.
- Select the height (first column) of the 124th baseball player in `np_baseball` and print it out.
```Python
import numpy as np

np_baseball = np.array(baseball)

# Print out the 50th row of np_baseball
print(np_baseball[49, :])
>>[ 70 195]

# Select the entire second column of np_baseball: np_weight_lb
np_weight_lb = np_baseball[:, 1]

# Print out height of 124th player
print(np_baseball[123, 0])
>>75
```