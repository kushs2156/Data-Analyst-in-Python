- Plot the distribution of `"Price"` column from `planes`.
- Display the descriptive statistics for flight duration.
```Python
# Plot a histogram of flight prices
sns.histplot(data=planes, x="Price")
plt.show()

# Display descriptive statistics for flight duration
print(planes["Duration"].describe())
```
![[download 106.svg]]
Which column potentially contains outliers?
- `Price` and `Duration`