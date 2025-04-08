Stratified sampling is a technique that allows us to sample a population that contains subgroups. For example, we could group the coffee ratings by country. If we count the number of coffees by country using the value_counts method, we can see that these six countries have the most data.
```Python
top_counts = coffee_ratings['country_of_origin'].value_counts()
top_counts.head(6)
>>country_of_origin
>>Mexico                      236
>>Colombia                    183
>>Guatemala                   181
>>Brazil                      132
>>Taiwan                       75
>>United States (Hawaii)       73
>>dtype: int64
```
To make it easier to think about sampling subgroups, let's limit our analysis to these six countries. We can use the `.isin()` method to filter the population and only return the rows corresponding to these six countries. This filtered dataset is stored as coffee_ratings_top.
```Python
top_counted_countries = ["Mexico", "Colombia", "Guatemala",
					"Brazil", "Taiwan", "United States (Hawaii)"]

top_counted_subset = coffee_ratings['country_of_origin'].isin( \ 
									top_counted_countries)

coffee_ratings_top = coffee_ratings[top_counted_subset]
```
Let's take a ten percent simple random sample of the dataset using .sample with frac set to 0.1. We also set the random_state argument to ensure reproducibility. As with the whole dataset, we can look at the counts for each country. To make comparisons easier, we set normalize to True to convert the counts into a proportion, which shows what proportion of coffees in the sample came from each country.
```Python
coffee_ratings_samp = coffee_ratings_top.sample(frac=0.1, 
												random_state=2021)
coffee_ratings_samp['country_of_origin'].value_counts(normalize=True)
```
Here are the proportions for the population and the 10% sample side by side. Just by chance, in this sample, Taiwanese coffees form a disproportionately low percentage. The different makeup of the sample compared to the population could be a problem if we want to analyse the country of origin, for example.
## Proportional stratified sampling
If we care about the proportions of each country in the sample closely matching those in the population, then we can group the data by country before taking the simple random sample. Note that we used the Python line continuation backslash here, which can be useful for breaking up longer chains of pandas code like this. Calling the .sample method after grouping takes a simple random sample within each country. 
```Python
coffee_ratings_strat = coffee_ratings_top.groupby("country_of_origin")\
		.sample(frac=0.1, random_state=2021)
coffee_ratings_strat['country_of_origin'].value_counts(normalize=True)
```
Now the proportions of each country in the stratified sample are much closer to those in the population.
## Equal counts stratified sampling
One variation of stratified sampling is to sample equal counts from each group, rather than an equal proportion. The code only has one change from before. This time, we use the n argument in .sample instead of frac to extract fifteen randomly-selected rows from each country. 
```Python
coffee_ratings_strat = coffee_ratings_top.groupby("country_of_origin")\
		.sample(n=15, random_state=2021)
coffee_ratings_strat['country_of_origin'].value_counts(normalize=True)
```
Here, the resulting sample has equal proportions of one-sixth from each country.
## Weighted random sampling
A close relative of stratified sampling that provides even more flexibility is weighted random sampling. In this variant, we create a column of weights that adjust the relative probability of sampling each row. For example, suppose we thought that it was important to have a higher proportion of Taiwanese coffees in the sample than in the population. We create a condition, in this case, rows where the country of origin is Taiwan. Using the where function from NumPy, we can set a weight of two for rows that match the condition and a weight of one for rows that don't match the condition. 
```Python
import numpy as np
coffee_ratings_weight = coffee_ratings_top
condition = coffee_ratings_weight['country_of_origin'] == "Taiwan"

coffee_ratings_weight['weight'] = np.where(condition, 2, 1)
```
This means when each row is randomly sampled, Taiwanese coffees have two times the chance of being picked compared to other coffees. When we call .sample, we pass the column of weights to the weights argument.
```Python
coffee_ratings_weight = coffee_ratings_weight.sample( \ 
						 frac=0.1, weights="weight")
```
Here, we can see that Taiwan now contains 17% of the sampled dataset, compared to 8.5% in the population. This sort of weighted sampling is common in political polling, where we need to correct for under- or over-representation of demographic groups.
## Let's practice!
Time to try these new techniques out!