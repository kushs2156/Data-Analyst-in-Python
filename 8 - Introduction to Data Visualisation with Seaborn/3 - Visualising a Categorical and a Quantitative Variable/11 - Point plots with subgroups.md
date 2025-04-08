- Use `sns.catplot()` and the `student_data` DataFrame to create a point plot with relationship status (`"romantic"`) on the x-axis and number of absences (`"absences"`) on the y-axis. Color the points based on the school that they attend (`"school"`).
```Python
# Create a point plot that uses color to create subgroups
sns.catplot(x="romantic", y="absences", data=student_data, 
			kind="point", hue="school")

# Show plot
plt.show()
```
![[download 83.svg]]
- Turn off the confidence intervals for the plot.
```Python
# Turn off the confidence intervals for this plot
sns.catplot(x="romantic", y="absences",
            data=student_data,
            kind="point",
            hue="school", ci=None)
            
# Show plot
plt.show()
```
![[download 84.svg]]
- Since there may be outliers of students with many absences, use the `median` function that we've imported from `numpy` to display the median number of absences instead of the average.
```Python
# Import median function from numpy
from numpy import median

# Plot the median number of absences instead of the mean
sns.catplot(x="romantic", y="absences",
            data=student_data,
            kind="point",
            hue="school",
            ci=None,
            estimator=median)

# Show plot
plt.show()
```
![[download 85.svg]]
