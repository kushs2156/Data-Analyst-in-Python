- _Look at `temperatures`_.
- Set the index of `temperatures` to `"city"`, assigning to `temperatures_ind`.
- _Look at `temperatures_ind`. How is it different from `temperatures`?_
- Reset the index of `temperatures_ind`, keeping its contents.
- Reset the index of `temperatures_ind`, dropping its contents.
```Python
# Look at temperatures
print(temperatures)

# Set the index of temperatures to city
temperatures_ind = temperatures.set_index("city")

# Look at temperatures_ind
print(temperatures_ind)

# Reset the temperatures_ind index, keeping its contents
print(temperatures_ind.reset_index())

# Reset the temperatures_ind index, dropping its contents
print(temperatures_ind.reset_index(drop=True))
```
