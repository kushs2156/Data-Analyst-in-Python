- You managed to get hold of the changes in height, weight and age of all baseball players. It is available as a 2D `numpy` array, `updated`. Add `np_baseball` and `updated` and print out the result.
- You want to convert the units of height and weight to metric (meters and kilograms, respectively). As a first step, create a `numpy` array with three values: `0.0254`, `0.453592` and `1`. Name this array `conversion`.
- Multiply `np_baseball` with `conversion` and print out the result.
```Python
import numpy as np

np_baseball = np.array(baseball)

# Print out addition of np_baseball and updated
print(np_baseball + updated)
>>[[ 75.2303559 168.83775102 23.99  ] 
>> [ 75.02614252 231.09732309 35.69 ] 
>> [ 73.1544228 215.08167641 31.78  ] 
>> ... 
>> [ 76.09349925 209.23890778 26.19 ] 
>> [ 75.82285669 172.21799965 32.01 ] 
>> [ 73.99484223 203.14402711 28.92 ]]

# Create numpy array: conversion
conversion = np.array([0.0254, 0.453592, 1])

# Print out product of np_baseball and conversion
print(np_baseball * conversion)
>>[[ 1.8796 81.64656 22.99 ] 
>> [ 1.8796 97.52228 34.69 ] 
>> [ 1.8288 95.25432 30.78 ] 
>> ... 
>> [ 1.905 92.98636 25.19  ] 
>> [ 1.905 86.18248 31.01  ] 
>> [ 1.8542 88.45044 27.92 ]]
```