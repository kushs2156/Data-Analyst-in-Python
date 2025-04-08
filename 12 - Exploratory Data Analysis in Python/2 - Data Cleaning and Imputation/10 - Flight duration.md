- Print the first five values of the `"Duration"` column.
- Remove `"h"` from the column.
- Convert the column to `float` data type.
```Python
# Preview the column
print(planes["Duration"].head())

# Remove the string character
planes["Duration"] = planes["Duration"].str.replace("h", "")

# Convert to float data type
planes["Duration"] = planes["Duration"].astype(float)

# Plot a histogram
sns.histplot(data=planes, x="Duration")
plt.show()
```
![[download 105.svg]]
