- Use `sns.catplot()` and the `student_data` DataFrame to create a point plot with `"famrel"` on the x-axis and number of absences (`"absences"`) on the y-axis.
```Python
# Create a point plot of family relationship vs. absences
sns.catplot(x="famrel", y="absences", data=student_data, kind="point")

# Show plot
plt.show()
```
![[download 80.svg]]
- Add "caps" to the end of the confidence intervals with size `0.2`.
```Python
# Add caps to the confidence interval
sns.catplot(x="famrel", y="absences",
            data=student_data,
            kind="point", capsize=0.2)
            
# Show plot
plt.show()
```
![[download 81.svg]]
- Remove the lines joining the points in each category.
```Python
# Remove the lines joining the points
sns.catplot(x="famrel", y="absences",
            data=student_data,
            kind="point",
            capsize=0.2, join=False)

# Show plot
plt.show()
```
![[download 82.svg]]
