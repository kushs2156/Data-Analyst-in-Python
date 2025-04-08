- Create a `seaborn` scatterplot (without a trendline) showing the relationship between `gdp_per_cap` (on the x-axis) and `life_exp` (on the y-axis).
- Show the plot
- Calculate the correlation between `gdp_per_cap` and `life_exp` and store as `cor`.
```Python
# Scatterplot of gdp_per_cap and life_exp
sns.scatterplot(x='gdp_per_cap', y='life_exp', data=world_happiness)

# Show plot
plt.show()

# Correlation between gdp_per_cap and life_exp
cor = world_happiness['gdp_per_cap'].corr(world_happiness['life_exp'])

print(cor)
```
![[download 44.svg]]
The correlation between GDP per capita and life expectancy is 0.7. Why is correlation **_not_** the best way to measure the relationship between these two variables?
- Correlation only measures linear relationships.