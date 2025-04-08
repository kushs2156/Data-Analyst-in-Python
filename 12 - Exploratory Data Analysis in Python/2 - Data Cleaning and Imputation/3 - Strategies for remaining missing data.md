- Print the values and frequencies of `"Additional_Info"`.
- Create a boxplot of `"Price"` versus `"Airline"`.
```Python
# Check the values of the Additional_Info column
print(planes["Additional_Info"].value_counts())

# Create a box plot of Price by Airline
sns.boxplot(data=planes, x="Airline", y="Price")

plt.show()
```
![[download 103.svg]]
- How should you deal with the missing values in `"Additional_Info"` and `"Price"`?
- Remove the `Additional_Info` column and impute the median by `Airline` for missing values of `Price`.