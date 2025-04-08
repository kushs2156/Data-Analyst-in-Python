Getting a sense of relationships between variables is important for evaluating how data should be used. That's where correlation comes in!
## Correlation
Correlation describes the direction of the relationship between two variables as well as its strength. Understanding this relationship can help us use variables to predict future outcomes. A quick way to see the pairwise correlation of numeric columns in a DataFrame is to use pandas' `.corr()` method. 
```Python
divorce.corr()
```
A negative correlation coefficient indicates that as one variable increases, the other decreases. A value closer to zero is indicative of a weak relationship, while values closer to one or negative one indicate stronger relationships. Note that .corr() calculates the Pearson correlation coefficient, measuring the **linear** relationship between two variables.
## Correlation heatmaps
Let's wrap our divorce.corr results in a Seaborn heatmap for quick visual interpretation. A heatmap has the benefit of colour coding so that strong positive and negative correlations, represented in deep purple and beige respectively, are easier to spot. Setting the annot argument to True labels the correlation coefficient inside each cell. 
```Python
sns.heatmap(divorce.corr(), annot=True)
plt.show()
```
Here, we can see that marriage year and marriage duration are strongly negatively correlated; in our dataset, marriages in later years are typically shorter.
## Correlation in context
However, this highlights an important point about correlations: we must always interpret them within the context of our data! Since our dataset is about marriages that ended between 2000 to 2015, marriages that started in earlier years will by definition have a longer duration than those that started in later ones.
```Python
divorce["divorce_date"].min()
>>Timestamp('2000-01-08 00:00:00')

divorce["divorce_date"].max()
>>Timestamp('2015-11-03 00:00:00')
```
## Visualising relationships
We also need to be careful to remember that the Pearson coefficient we've been looking at only describes the linear correlation between variables. Variables can have a strong non-linear relationship and a Pearson correlation coefficient of close to zero. Alternatively, data might have a correlation coefficient indicating a strong linear relationship when another relationship, such as quadratic, is actually a better fit for the data. This is why it's important to complement our correlation calculations with scatter plots!
## Scatter plots
For example, the monthly income of the female partner and the male partner at the time of divorce showed a correlation coefficient of 0.32 in our heatmap. Let's check that this correctly indicates a small positive relationship between the two variables by passing them as x and y arguments to Seaborn's scatterplot function. 
```Python
sns.scatterplot(data=divorce, x="income_man", y="income_woman")
```
It looks like the relationship exists but is not particularly strong, just as our heatmap suggested.
## Pairplots
We can take our scatterplots to the next level with Seaborn's pairplot. When passed a DataFrame, pairplot plots all pairwise relationships between numerical variables in one visualisation. On the diagonal from upper left to lower right, we see the distribution of each variable's observations. This is useful for a quick overview of relationships within the dataset. However, having this much information in one visual can be difficult to interpret, especially with big datasets which lead to very small plot labels like the ones we see here.
```Python
sns.pairplot(data=divorce)
plt.show()

sns.pairplot(data=divorce, vars=["income_man", "income_woman",
								 "marriage_duration"])
plt.show()
```
We can limit the number of plotted relationships by setting the vars argument equal to the variables of interest. This visual reassures us that what our correlation coefficients told us was true: variables representing the income of each partner as well as the marriage duration variable all have fairly weak relationships with each other. We also notice in the lower right plot that the distribution of marriage durations includes many shorter marriages and fewer longer marriages.
## Let's practice!
Now it's your turn to search for relationships in the divorce dataset!