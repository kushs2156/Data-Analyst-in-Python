- Use `print()` in combination with `type()` to print out the type of `var1`.
- Use `len()` to get the [length of the list](https://docs.python.org/3/library/functions.html#len) `var1`. Wrap it in a `print()` call to directly print it out.
- Use `int()` to convert `var2` to an [integer](https://docs.python.org/3/library/functions.html#int). Store the output as `out2`.
```Python
# Create variables var1 and var2
var1 = [1, 2, 3, 4]
var2 = True

# Print out type of var1
print(type(var1))
>><class 'list'>

# Print out length of var1
print(len(var1))
>>4

# Convert var2 to an integer: out2
out2 = int(var2)
```