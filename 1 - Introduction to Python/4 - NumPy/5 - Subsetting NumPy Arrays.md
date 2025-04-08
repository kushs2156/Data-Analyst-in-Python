- Subset `np_weight_lb` by printing out the element at index 50.
- Print out a sub-array of `np_height_in` that contains the elements at index 100 up to **and including** index 110.
```Python
import numpy as np

np_weight_lb = np.array(weight_lb)
np_height_in = np.array(height_in)

# Print out the weight at index 50
print(np_weight_lb[50])
>>200

# Print out sub-array of np_height_in: index 100 up to and including index 110
print(np_height_in[100:111])
>>[73 74 72 73 69 72 73 75 75 73 72]
```