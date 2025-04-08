- Produce a barplot comparing `"Salary_USD"` by `"Company_Size"`, factoring `"Employment_Status"`.
```Python
# Create a bar plot of salary versus company size, factoring in employment status
sns.barplot(data=salaries, x="Company_Size", y="Salary_USD", 
				hue="Employment_Status")
plt.show()
```
![[download 117.svg]]
What is a reasonable hypothesis to generate based on this plot?
- On average, large companies pay contractors more than medium-sized companies.