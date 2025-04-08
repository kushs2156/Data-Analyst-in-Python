- Import `matplotlib.pyplot` with the alias `plt`.
- Subset `food_consumption` to get the rows where `food_category` is `'rice'`.
- Create a histogram of `co2_emission` in `rice_consumption` DataFrame and show the plot.
```Python
# Import matplotlib.pyplot with alias plt
import matplotlib.pyplot as plt

# Subset for food_category equals rice
rice_consumption = food_consumption[food_consumption['food_category'] == 'rice']

# Histogram of co2_emission for rice and show plot
plt.hist(x=rice_consumption['co2_emission'])
plt.show()
```
![[download 33.svg]]
Take a look at the histogram you just created of different countries' CO2 emissions for rice. Which of the following terms best describes the shape of the data?
- Right-skewed

- Use `.agg()` to calculate the mean and median of `co2_emission` for rice.
```Python
# Subset for food_category equals rice
rice_consumption = food_consumption[food_consumption['food_category'] 
											== 'rice']

# Calculate mean and median of co2_emission with .agg()
print(rice_consumption['co2_emission'].agg([np.mean, np.median]))
>>mean 37.592 
>>median 15.200 
>>Name: co2_emission, dtype: float64
```
Given the skew of this data, what measure of central tendency best summarizes the kilograms of CO2 emissions per person per year for rice?
- Median