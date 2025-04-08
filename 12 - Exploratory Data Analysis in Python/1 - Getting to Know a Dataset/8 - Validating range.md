- Print the minimum and maximum unemployment rates, in that order, during 2021.
- Create a boxplot of 2021 unemployment rates (on the x-axis), broken down by continent (on the y-axis).
```Python
# Print the minimum and maximum unemployment rates during 2021
print(unemployment["2021"].min(), unemployment["2021"].max())

# Create a boxplot of 2021 unemployment rates, broken down by continent
sns.boxplot(data=unemployment, x="2021", y="continent")
plt.show()
```
![[download 101.svg]]
