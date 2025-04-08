- Modify the code to use `relplot()` instead of `scatterplot()`.
- Modify the code to create one scatter plot for each level of the variable `"study_time"`, arranged in columns.
- Adapt your code to create one scatter plot for each level of a student's weekly study time, this time arranged in rows.
```Python
# Change to use relplot() instead of scatterplot()
sns.relplot(x="absences", y="G3", 
                data=student_data, kind="scatter")

# Show plot
plt.show()
```
![[download 54.svg]]
```Python
# Change to make subplots based on study time
sns.relplot(x="absences", y="G3", data=student_data,
            kind="scatter", col="study_time")

# Show plot
plt.show()
```
![[download 55.svg]]
```Python
# Change this scatter plot to arrange the plots in rows instead of columns
sns.relplot(x="absences", y="G3", data=student_data,
            kind="scatter", row="study_time")

# Show plot
plt.show()
```
![[download 56.svg]]
