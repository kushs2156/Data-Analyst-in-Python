- Use `relplot()` to create a scatter plot with `"G1"` on the x-axis and `"G3"` on the y-axis, using the `student_data` DataFrame.
- Create **column** subplots based on whether the student received support from the school (`"schoolsup"`), ordered so that "yes" comes before "no".
- Add **row** subplots based on whether the student received support from the family (`"famsup"`), ordered so that "yes" comes before "no". This will result in subplots based on two factors.
```Python
# Create a scatter plot of G1 vs. G3
sns.relplot(x="G1", y="G3", data=student_data, kind="scatter")

# Show plot
plt.show()
```
![[download 57.svg]]
```Python
# Adjust to add subplots based on school support
sns.relplot(x="G1", y="G3", data=student_data,kind="scatter",
            col="schoolsup", col_order=["yes", "no"])

# Show plot
plt.show()
```
![[download 58.svg]]
```Python
# Adjust further to add subplots based on family support
sns.relplot(x="G1", y="G3", data=student_data, kind="scatter", 
            col="schoolsup", col_order=["yes", "no"],
            row="famsup", row_order=["yes", "no"])

# Show plot
plt.show()
```
![[download 59.svg]]
