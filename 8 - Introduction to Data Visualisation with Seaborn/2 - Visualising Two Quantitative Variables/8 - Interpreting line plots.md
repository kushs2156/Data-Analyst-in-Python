- Use `relplot()` and the `mpg` DataFrame to create a line plot with `"model_year"` on the x-axis and `"mpg"` on the y-axis.
```Python
# Import Matplotlib and Seaborn
import matplotlib.pyplot as plt
import seaborn as sns

# Create line plot
sns.relplot(x="model_year", y="mpg", data=mpg, kind="line")

# Show plot
plt.show()
```
![[download 63.svg]]
Which of the following is NOT a correct interpretation of this line plot?
- The distribution of miles per gallon is smaller in 1973 compared to 1977.
  (The shaded region represented a confidence interval for the mean, not the distribution of the observations.)