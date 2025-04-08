- Use `.append()` twice to add the size of the poolhouse and the garage again: `24.5` and `15.45`, respectively. Make sure to add them in this order.
- Print out `areas`
- Use the `.reverse()` method to reverse the order of the elements in `areas`.
- Print out `areas` once more.
```Python
# Create list areas
areas = [11.25, 18.0, 20.0, 10.75, 9.50]

# Use append twice to add poolhouse and garage size
areas.append(24.5)
areas.append(15.45)

# Print out areas
print(areas)
>>[11.25, 18.0, 20.0, 10.75, 9.5, 24.5, 15.45]

# Reverse the orders of the elements in areas
areas.reverse()

# Print out areas
print(areas)
>>[15.45, 24.5, 9.5, 10.75, 20.0, 18.0, 11.25]
```
