- Filter `salaries` where `"Employee_Location"` is `"US"` _or_ `"GB"`, saving as `usa_and_gb`.
- Use `usa_and_gb` to create a barplot visualizing `"Salary_USD"` against `"Employee_Location"`.
```Python
# Filter for employees in the US or GB
usa_and_gb = salaries[salaries["Employee_Location"].isin(["US", "GB"])]

# Create a barplot of salaries by location
sns.barplot(data=usa_and_gb, x="Employee_Location", y="Salary_USD")
plt.show()
```
![[download 116.svg]]
