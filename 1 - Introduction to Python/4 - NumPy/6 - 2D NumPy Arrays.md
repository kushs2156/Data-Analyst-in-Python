Well done you legend! Let's now recreate the NumPy arrays from the previous video.
## Type of NumPy Arrays

```Python
import numpy as np
np_height = np.array(height)
np_weight = np.array(weight)
```
```Python
type(np_height)
numpy.darray
type(np_weight)
numpy.darray
```
If you ask for the type of these arrays, Python tells you that they are   `numpy.ndarray`. numpy. tells you it's a type that was defined in the numpy package. ndarray stands for n-dimensional array. The arrays np_height and np_weight are one-dimensional arrays, but it's perfectly possible to create 2 dimensional, three dimensional, heck even seven dimensional arrays! Let's stick to 2 in this video though.
## 2D NumPy Arrays
You can create a 2D NumPy array from a regular Python list of lists. Let's try to create one NumPy array for all height and weight data of your family.
```Python
np_2d = np.array([[1.73, 1.68, 1.71, 1.89, 1.79],
				  [65.4, 59.2, 63.6, 88.4, 68.7]])
```
If you print out np_2d now, you'll see that it is a rectangular data structure: Each sublist in the list, corresponds to a row in the two dimensional NumPy array. From `np_2d.shape`, you can see that we indeed have 2 rows and 5 columns. **shape** is a so-called attribute of the np_2d array, that can give you more information about what the data structure looks like. Note that the syntax for accessing an attribute looks a bit like calling a method, but they are not the same! Remember that methods have round brackets after them, and, you can see here, attributes do not. Also for 2D arrays, the NumPy rule applies: an array can only contain a single type. If you change one float to be string, all the array elements will be coerced to strings, to end up with a homogeneous array.
## Subsetting
You can think of the 2D NumPy array as an improved list of lists: you can perform calculations on the arrays, like I showed before, and you can do more advanced ways of subsetting. Suppose you want the first row, and then the third element in that row. To select the row, you need the index 0 in square brackets. Don't forget about zero indexing. To then select the third element, you can extend the same call with another pair of brackets, this time with the index 2:
```Python
np_2d[0][2]
>>1.71
```
Basically you're selecting the row, and then from that row do another selection. There's also an alternative way of subsetting, using single square brackets and a comma. This call returns the exact same value as before. 
```Python
np_2d[0, 2]
>>1.71
```
The value before the comma specifies the row, the value after the comma specifies the column. The intersection of the rows and columns you specified, are returned. Once you get used to it, this syntax is more intuitive and opens up more possibilities.

Suppose you want to select the height and weight of the second and third family member. You want both rows, so you put in a colon before the comma. You only want the second and third column, so you put in the indices 1 to 3 after the comma. Remember that the third index is not included here. 
```Python
np_2d[:, 1:3]
>>array([[1.68, 1.71],
         [59.2, 63.6]])
```
The intersection gives us a 2D array with 2 rows and 2 columns: Similarly, you can select the weight of all family members like this: you only want the second row, so put 1 before the comma. You want all columns, so you use a colon after the comma. The intersection gives us the entire second row. 
```Python
np_2d[1, :]
>>array([65.4, 59.2, 63.6, 88.4, 68.7])
```
Finally, 2D NumPy arrays enable you to do element-wise calculations, the same way you did it with 1D NumPy arrays. That's something you can experiment with in the exercises, along with creating and subsetting 2D NumPy arrays! 
