- Use `sns.catplot()` to create a count plot using the `survey_data` DataFrame with `"Internet usage"` on the x-axis.
```Python
# Create count plot of internet usage
sns.catplot(x="Internet usage", data=survey_data, kind="count")

# Show plot
plt.show()
```
![[download 68.svg]]
- Make the bars horizontal instead of vertical.
```Python
# Change the orientation of the plot
sns.catplot(y="Internet usage", data=survey_data, kind="count")

# Show plot
plt.show()
```
![[download 69.svg]]
- Separate this plot into two side-by-side column subplots based on `"Age Category"`, which separates respondents into those that are younger than 21 vs. 21 and older.
```Python
# Separate into column subplots based on age category
sns.catplot(y="Internet usage", data=survey_data,
            kind="count", col="Age Category")
            
# Show plot
plt.show()
```
![[download 70.svg]]
