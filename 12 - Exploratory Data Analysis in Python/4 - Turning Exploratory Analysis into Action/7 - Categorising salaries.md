- Create `salary_labels`, a list containing `"entry"`, `"mid"`, `"senior"`, and `"exec"`.
- Finish `salary_ranges`, adding the 25th percentile, median, 75th percentile, and largest value from `"Salary_USD"`.
- Split `"Salary_USD"` based on the labels and ranges you've created.
- Use `sns.countplot()` to visualise the count of `"Company_Size"`, factoring salary level labels.
```Python
# Create salary labels
salary_labels = ["entry", "mid", "senior", "exec"]

# Create the salary ranges list
salary_ranges = [0, twenty_fifth, salaries_median, seventy_fifth, 
				 salaries["Salary_USD"].max()]

# Create salary_level
salaries["salary_level"] = pd.cut(salaries["Salary_USD"],
                                  bins=salary_ranges,
                                  labels=salary_labels)

# Plot the count of salary levels at companies of different sizes
sns.countplot(data=salaries, x="Company_Size", hue="salary_level")
plt.show()
```
![[download 115.svg]]
