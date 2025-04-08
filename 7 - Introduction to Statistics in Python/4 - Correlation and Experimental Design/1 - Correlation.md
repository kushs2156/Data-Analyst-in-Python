Welcome to the final chapter of the course, where we'll talk about correlation and experimental design.
## Relationships between two variables
Before we dive in, let's talk about relationships between numeric variables. We can visualise these kinds of relationships with scatter plots - in this scatterplot, we can see the relationship between the total amount of sleep mammals get and the amount of REM sleep they get. The variable on the x-axis is called the explanatory or independent variable, and the variable on the y-axis is called the response or dependent variable.
## Correlation coefficient
We can also examine relationships between two numeric variables using a number called the correlation coefficient. This is a number between -1 and 1, where the magnitude corresponds to the strength of the relationship between the variables, and the sign, positive or negative, corresponds to the direction of the relationship. 

Here's a scatterplot of 2 variables, x and y, that have a correlation coefficient of 0.99. Since the data points are closely clustered around a line, we can describe this as a near-perfect or very strong relationship. If we know what x is, we'll have a pretty good idea of what the value of y could be. Here, x and y have a correlation coefficient of 0.75, and the data points are a bit more spread out. In this plot, x and y have a correlation of 0.56 and are therefore moderately correlated. A correlation coefficient around 0.2 would be considered a weak relationship. When the correlation coefficient is close to 0, x and y have no relationship and the scatterplot looks completely random. This means that knowing the value of x doesn't tell us anything about the value of y. The sign of the correlation coefficient corresponds to the direction of the relationship. A positive correlation coefficient indicates that as x increases, y also increases. A negative correlation coefficient indicates that as x increases, y decreases.
## Visualising relationships
To visualise relationships between two variables, we can use a scatterplot. We'll use seaborn, which is a plotting package built on top of matplotlib. We import seaborn as sns, which is the alias commonly used for seaborn. We create a scatterplot using `sns.scatterplot`, passing it the name of the variable for the x-axis, the name of the variable for the y-axis, as well as the msleep DataFrame to the data argument. Finally, we call `plt.show()`.
```Python
import seaborn as sns
sns.scatterplot(x="sleep_total", y="sleep_rem", data=msleep)
plt.show()

sns.lmplot(x="sleep_total", y="sleep_rem", data=msleep, ci=None)
plt.show()
```
We can add a linear trendline to the scatterplot using seaborn's lmplot() function. It takes the same arguments as sns-dot-scatterplot, but we'll set ci to None so that there aren't any confidence interval margins around the line. Trendlines like this can be helpful to more easily see a relationship between two variables.
## Computing correlation
To calculate the correlation coefficient between two Series, we can use the `.corr()` method. If we want the correlation between the sleep_total and sleep_rem columns of msleep, we can take the sleep_total column and call `.corr()` on it, passing in the other Series we're interested in. 
```Python
msleep['sleep_total'].corr(msleep['sleep_rem'])
>>0.751755

msleep['sleep_rem'].corr(msleep['sleep_total'])
>>0.751755
```
Note that it doesn't matter which Series the method is invoked on and which is passed in since the correlation between x and y is the same thing as the correlation between y and x.
## Many ways to calculate correlation
There's more than one way to calculate correlation, but the method we've been using in this video is called the Pearson product-moment correlation, which is also written as $r$. This is the most commonly used measure of correlation. Mathematically, it's calculated using this formula:
$$
r = \sum_{i=1}^{n}{\frac{(x_{i} - \bar{x})(y_{i} - \bar{y})}{\sigma_{x} \times \sigma_{y}}}
$$
where $\bar{x}$ and $\bar{y}$ are the means of x and y, and $\sigma_x$ and $\sigma_y$ are the standard deviations of x and y. The formula itself isn't important to memorise, but know that there are variations of this formula that measure correlation a bit differently, such as Kendall's tau and Spearman's rho, but those are beyond the scope of this course.
## Let's practice!
Okay, time to practice calculating correlations.