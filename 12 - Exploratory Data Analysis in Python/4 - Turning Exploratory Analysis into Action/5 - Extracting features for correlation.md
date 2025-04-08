- Extract the month from `"date_of_response"`, storing it as a column called `"month"`.
- Create the `"weekday"` column, containing the weekday that the participants completed the survey.
- Plot a heat map, including the Pearson correlation coefficient scores.
```Python
# Get the month of the response
salaries["month"] = salaries["date_of_response"].dt.month

# Extract the weekday of the response
salaries["weekday"] = salaries["date_of_response"].dt.weekday

# Create a heatmap
sns.heatmap(salaries.corr(), annot=True)
plt.show()
```
![[download 114.svg]]
