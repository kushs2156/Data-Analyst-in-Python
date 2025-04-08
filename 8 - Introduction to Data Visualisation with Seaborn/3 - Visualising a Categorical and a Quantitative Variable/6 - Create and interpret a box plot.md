- Use `sns.catplot()` and the `student_data` DataFrame to create a box plot with `"study_time"` on the x-axis and `"G3"` on the y-axis. Set the ordering of the categories to `study_time_order`.
```Python
# Specify the category ordering
study_time_order = ["<2 hours", "2 to 5 hours", 
                    "5 to 10 hours", ">10 hours"]

# Create a box plot and set the order of the categories
sns.catplot(x="study_time", y="G3", data=student_data, 
			kind="box", order=study_time_order)

# Show plot
plt.show()
```
![[download 75.svg]]
Which of the following is a correct interpretation of this box plot?
- The median grade among students studying less than 2 hours in 10.0.