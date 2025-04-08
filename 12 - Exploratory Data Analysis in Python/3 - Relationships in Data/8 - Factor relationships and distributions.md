- Create a pairplot to visualise the relationships between `income_woman` and `marriage_duration` in the `divorce` DataFrame.
```Python
# Create a pairplot for income_woman and marriage_duration
sns.pairplot(data=divorce, vars=["income_woman" , "marriage_duration"])
plt.show()
```
![[download 109.svg]]
