- Print a DataFrame that shows whether each value in `avocados_2016` is missing or not.
- Print a summary that shows whether _any_ value in each column is missing or not.
- Create a bar plot of the total number of missing values in each column.
```Python
# Import matplotlib.pyplot with alias plt
import matplotlib.pyplot as plt

# Check individual values for missing values
print(avocados_2016.isna())

# Check each column for missing values
print(avocados_2016.isna().any())

# Bar plot of missing values by variable
avocados_2016.isna().sum().plot(kind="bar")

# Show plot
plt.show()
```
![[download 24.svg]]
