- Fill in the `palette_colors` dictionary to map the `"Rural"` location value to the color `"green"` and the `"Urban"` location value to the color `"blue"`.
- Create a count plot with `"school"` on the x-axis using the `student_data` DataFrame.
    - Add subgroups to the plot using `"location"` variable and use the `palette_colors` dictionary to make the location subgroups green and blue.
```Python
# Import Matplotlib and Seaborn
import matplotlib.pyplot as plt
import seaborn as sns

# Create a dictionary mapping subgroup values to colors
palette_colors = {"Rural": "green", "Urban": "blue"}

# Create a count plot of school with location subgroups
sns.countplot(x="school", data=student_data, hue="location", 
				palette=palette_colors)

# Display plot
plt.show()
```
![[download 53.svg]]
