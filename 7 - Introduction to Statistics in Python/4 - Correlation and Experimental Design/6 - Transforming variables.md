- Create a scatterplot of `happiness_score` versus `gdp_per_cap` and calculate the correlation between them.
```Python
# Scatterplot of happiness_score vs. gdp_per_cap
sns.scatterplot(x='gdp_per_cap', y='happiness_score', 
					data=world_happiness)
plt.show()

# Calculate correlation
cor = world_happiness['happiness_score'].corr(
						world_happiness['gdp_per_cap'])
print(cor)
```
![[download 45.svg]]
- Add a new column to `world_happiness` called `log_gdp_per_cap` that contains the log of `gdp_per_cap`.
- Create a `seaborn` scatterplot of `happiness_score` versus `log_gdp_per_cap`.
- Calculate the correlation between `log_gdp_per_cap` and `happiness_score`.
```Python
# Create log_gdp_per_cap column
world_happiness['log_gdp_per_cap'] = np.log(
								world_happiness['gdp_per_cap'])

# Scatterplot of happiness_score vs. log_gdp_per_cap
sns.scatterplot(x='log_gdp_per_cap', y='happiness_score', 
								data=world_happiness)
plt.show()

# Calculate correlation
cor = world_happiness['log_gdp_per_cap'].corr(
						world_happiness['happiness_score'])
print(cor)
```
![[download 46.svg]]
