- Use `relplot()` and the `mpg` DataFrame to create a line plot with `"model_year"` on the x-axis and `"horsepower"` on the y-axis. Turn off the confidence intervals on the plot.
```Python
# Import Matplotlib and Seaborn
import matplotlib.pyplot as plt
import seaborn as sns

# Create line plot of model year vs. horsepower
sns.relplot(x="model_year", y="horsepower", data=mpg, kind="line", ci=None)

# Show plot
plt.show()
```
![[download 65.svg]]
- Create different lines for each country of origin (`"origin"`) that vary in both line style and colours.
```Python
# Import Matplotlib and Seaborn
import matplotlib.pyplot as plt
import seaborn as sns

# Change to create subgroups for country of origin
sns.relplot(x="model_year", y="horsepower", data=mpg, kind="line", 
            ci=None, style="origin", hue="origin")
            
# Show plot
plt.show()
```
![[download 66.svg]]
- Add markers for each data point to the lines.
- Use the `dashes` parameter to use solid lines for all countries, while still allowing for different marker styles for each line.
```Python
# Import Matplotlib and Seaborn
import matplotlib.pyplot as plt
import seaborn as sns

# Add markers and make each line have the same style
sns.relplot(x="model_year", y="horsepower", data=mpg, kind="line", 
            ci=None, style="origin", hue="origin", 
            markers=True, dashes=False)

# Show plot
plt.show()
```
![[download 67.svg]]
