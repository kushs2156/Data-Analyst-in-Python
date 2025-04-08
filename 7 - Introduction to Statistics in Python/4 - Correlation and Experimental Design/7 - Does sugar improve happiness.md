- Create a `seaborn` scatterplot showing the relationship between `grams_sugar_per_day` (on the x-axis) and `happiness_score` (on the y-axis).
- Calculate the correlation between `grams_sugar_per_day` and `happiness_score`.
```Python
# Scatterplot of grams_sugar_per_day and happiness_score
sns.scatterplot(x='grams_sugar_per_day', y='happiness_score', 
						data=world_happiness)
plt.show()

# Correlation between grams_sugar_per_day and happiness_score
cor = world_happiness['grams_sugar_per_day'].corr(
						world_happiness['happiness_score'])
print(cor)
```
![[download 47.svg]]
Based on this data, which statement about sugar consumption and happiness scores is true?
- Increased sugar consumption is associated with a higher happiness score.