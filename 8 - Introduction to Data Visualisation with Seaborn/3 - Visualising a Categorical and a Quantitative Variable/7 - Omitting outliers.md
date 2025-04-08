- Use `sns.catplot()` to create a box plot with the `student_data` DataFrame, putting `"internet"` on the x-axis and `"G3"` on the y-axis.
- Add subgroups so each box plot is coloured based on `"location"`.
- Do not display the outliers.
```Python
# Create a box plot with subgroups and omit the outliers
sns.catplot(x="internet", y="G3", data=student_data, 
			kind="box", sym="", hue="location")

# Show plot
plt.show()
```
![[download 76.svg]]
