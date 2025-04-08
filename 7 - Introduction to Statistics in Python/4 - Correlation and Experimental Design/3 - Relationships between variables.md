- Create a scatterplot of `happiness_score` vs. `life_exp` (without a trendline) using `seaborn`.
- Show the plot.
```Python
# Create a scatterplot of happiness_score vs. life_exp and show
sns.scatterplot(x='life_exp', y='happiness_score', 
				data=world_happiness)

# Show plot
plt.show()
```
![[download 42.svg]]
- Create a scatterplot of `happiness_score` vs. `life_exp` **with a linear trendline** using `seaborn`, setting `ci` to `None`.
- Show the plot.
```Python
# Create scatterplot of happiness_score vs life_exp with trendline
sns.lmplot(x='life_exp', y='happiness_score', 
			data=world_happiness, ci=None)

# Show plot
plt.show()
```
![[download 43.svg]]
Based on the scatterplot, which is most likely the correlation between `life_exp` and `happiness_score`?
- 0.8

- Calculate the correlation between `life_exp` and `happiness_score`. Save this as `cor`.
```Python
# Correlation between life_exp and happiness_score
cor = world_happiness['life_exp'].corr(
							world_happiness['happiness_score'])

print(cor)
```
