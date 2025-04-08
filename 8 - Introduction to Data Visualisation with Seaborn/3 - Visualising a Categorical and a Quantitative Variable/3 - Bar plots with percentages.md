- Use the `survey_data` DataFrame and `sns.catplot()` to create a bar plot with `"Gender"` on the x-axis and `"Interested in Math"` on the y-axis.
```Python
# Create a bar plot of interest in math, separated by gender
sns.catplot(x="Gender", y="Interested in Math", 
			data=survey_data, kind="bar")

# Show plot
plt.show()
```
![[download 71.svg]]
