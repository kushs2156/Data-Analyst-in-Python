- Use `relplot()` and the `mpg` DataFrame to create a scatter plot with `"horsepower"` on the x-axis and `"mpg"` on the y-axis. Vary the size of the points by the number of cylinders in the car (`"cylinders"`).
```Python
# Import Matplotlib and Seaborn
import matplotlib.pyplot as plt
import seaborn as sns

# Create scatter plot of horsepower vs. mpg
sns.relplot(x="horsepower", y="mpg", data=mpg, kind="scatter", size="cylinders")

# Show plot
plt.show()
```
![[download 60.svg]]
- To make this plot easier to read, use `hue` to vary the color of the points by the number of cylinders in the car (`"cylinders"`).
```Python
# Import Matplotlib and Seaborn
import matplotlib.pyplot as plt
import seaborn as sns

# Create scatter plot of horsepower vs. mpg
sns.relplot(x="horsepower", y="mpg", data=mpg, kind="scatter", 
            size="cylinders", hue="cylinders")

# Show plot
plt.show()
```
![[download 61.svg]]
