- Print the head of the `avocados` dataset. _What columns are available?_
- For each avocado size group, calculate the total number sold, storing as `nb_sold_by_size`.
- Create a bar plot of the number of avocados sold by size.
- Show the plot.
```Python
# Import matplotlib.pyplot with alias plt
import matplotlib.pyplot as plt

# Look at the first few rows of data
print(avocados.head())

# Get the total number of avocados sold of each size
nb_sold_by_size = avocados.groupby("size")["nb_sold"].sum()

# Create a bar plot of the number of avocados sold by size
nb_sold_by_size.plot(kind="bar")

# Show the plot
plt.show()
```
![[download 18.svg]]

