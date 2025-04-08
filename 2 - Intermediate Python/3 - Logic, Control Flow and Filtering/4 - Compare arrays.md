- Which areas in `my_house` are greater than or equal to `18`?
- You can also compare two NumPy arrays element-wise. Which areas in `my_house` are smaller than the ones in `your_house`?
- Make sure to wrap both commands in a `print()` statement so that you can inspect the output!
```Python
# Create arrays
import numpy as np
my_house = np.array([18.0, 20.0, 10.75, 9.50])
your_house = np.array([14.0, 24.0, 14.25, 9.0])

# my_house greater than or equal to 18
print(my_house >= 18)
>>[ True True False False]

# my_house less than your_house
print(my_house < your_house)
>>[False True True False]
```
