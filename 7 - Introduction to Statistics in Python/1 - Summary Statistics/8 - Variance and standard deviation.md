- Calculate the variance and standard deviation of `co2_emission` for each `food_category` with the `.groupby()` and `.agg()` methods; compare the values of variance and standard deviation.
- Create a histogram of `co2_emission` for the `beef` in `food_category` and show the plot.
- Create a histogram of `co2_emission` for the `eggs` in `food_category` and show the plot.
```Python
# Print variance and sd of co2_emission for each food_category
print(food_consumption.groupby('food_category')['co2_emission'].agg([np.var, np.std]))

# Create histogram of co2_emission for food_category 'beef'
food_consumption[food_consumption['food_category'] == 'beef']['co2_emission'].hist()
plt.show()

# Create histogram of co2_emission for food_category 'eggs'
food_consumption[food_consumption['food_category'] == 'eggs']['co2_emission'].hist()
plt.show()
```
![[download 34.svg]]![[download 35.svg]]
