Let's review the various sampling techniques we learned about.
## Review of sampling techniques - setup
For convenience, we'll stick to the six countries with the most coffee varieties that we used before. This corresponds to 880 rows and eight columns, retrieved using the .shape attribute.
```Python
top_counted_countries = ["Mexico", "Colombia", "Guatemala", "Brazil",
						 "Taiwan", "United States (Hawaii)"]

subset_condition = coffee_ratings['country_of_origin'].isin( \ 
					top_counted_countries)
coffee_ratings_top = coffee_ratings[subset_condition]

coffee_ratings_top.shape
>>(880, 8)
```
## Review of simple random sampling
Simple random sampling uses .sample with either n or frac set to determine how many rows to pseudo-randomly choose, given a seed value set with random_state. The simple random sample returns 293 rows because we specified frac as one-third, and one-third of 880 is just over 293.
```Python
coffee_ratings_srs = coffee_ratings_top.sample(frac=1/3, 
											   random_state=2021)
coffee_ratings_srs.shape
>>(293, 8)
```
## Review of stratified sampling
Stratified sampling groups by the country subgroup before performing simple random sampling on each subgroup. Given each of these top countries have quite a few rows, stratifying produces the same number of rows as the simple random sample.
```Python
coffee_ratings_strat = coffee_ratings_top.groupby("country_of_origin")\
	.sample(frac=1/3, random_state=2021)
coffee_ratings_strat.shape
>>(293, 8)
```
## Review of cluster sampling
In the cluster sample, we've used two out of six countries to roughly mimic frac equals one-third from the other sample types. Setting n equal to one-sixth of the total number of rows gives roughly equal sample sizes in each of the two subgroups. Using .shape again, we see that this cluster sample has close to the same number of rows: 292 compared to 293 for the other sample types.
```Python
import random
top_countries_samp = random.sample(top_counted_countries, k=2)
top_condition = coffee_ratings_top['country_of_origin'].isin( \
	top_countries_samp)
coffee_ratings_cluster = coffee_ratings_top[top_condition]
coffee_ratings_cluster['country_of_origin'] = 
	coffee_ratings_cluster['country_of_origin'] \
		.cat.remove_unused_categories()

coffee_ratings_clust = coffee_ratings_cluster.groupby( \
	'country_of_origin').sample(n=len(coffee_ratings_top) // 6)

coffee_ratings_cluster.shape
>>(292, 8)
```
## Calculating mean cup points
Let's calculate a population parameter, the mean of the total cup points. When the population parameter is the mean of a field, it's often called the population mean. Remember that in real-life scenarios, we typically wouldn't know what the population mean is. Since we have it here, though, we can use this value of 81.9 as a gold standard to measure against. 
```Python
coffee_ratings_top['total_cup_points'].mean()
>>81.94700000000002

coffee_ratings_srs['total_cup_points'].mean()
>>81.95982935153583

coffee_ratings_strat['total_cup_points'].mean()
>>81.92566552901025

coffee_ratings_clust['total_cup_points'].mean()
>>82.03246575342466
```
Now we'll calculate the same value using each of the sampling techniques we've discussed. These are point estimates of the mean, often called sample means. The simple and stratified sample means are really close to the population mean. Cluster sampling isn't quite as close, but that's typical. Cluster sampling is designed to give us an answer that's almost as good while using less data.
## Mean cup points by country: simple random
Here's a slightly more complicated calculation of the mean total cup points for each country. We group by country before calculating the mean to return six numbers. So how do the numbers from the simple random sample compare? The sample means are pretty close to the population means.
```Python
coffee_ratings_top.groupby("country_of_origin")["total_cup_points"] \
	.mean()
>>country_of_origin
>>Brazil                   82.405909
>>Colombia                 83.106557
>>Guatemala                81.846575
>>Mexico                   80.890085
>>Taiwan                   82.001333
>>United States (Hawaii)   81.820411
>>Name: total_cup_points, dtype=float64

coffee_ratings_srs.groupby("country_of_origin")["total_cup_points"] \
	.mean()
>>country_of_origin
>>Brazil                   82.414878
>>Colombia                 82.925536
>>Guatemala                82.045385
>>Mexico                   81.100714
>>Taiwan                   81.744333
>>United States (Hawaii)   82.008000
>>Name: total_cup_points, dtype=float64
```
## Mean cup points by country: stratified
The same is true of the sample means from the stratified technique. Each sample mean is relatively close to the population mean.
```Python
coffee_ratings_top.groupby("country_of_origin")["total_cup_points"] \
	.mean()
>>country_of_origin
>>Brazil                   82.405909
>>Colombia                 83.106557
>>Guatemala                81.846575
>>Mexico                   80.890085
>>Taiwan                   82.001333
>>United States (Hawaii)   81.820411
>>Name: total_cup_points, dtype=float64

coffee_ratings_strat.groupby("country_of_origin")["total_cup_points"] \
	.mean()
>>country_of_origin
>>Brazil                   82.499773
>>Colombia                 83.288197
>>Guatemala                81.727667
>>Mexico                   80.994684
>>Taiwan                   81.846800
>>United States (Hawaii)   81.051667
>>Name: total_cup_points, dtype=float64
```
## Mean cup points by country: cluster
With cluster sampling, while the sample means are pretty close to the population means, the obvious limitation is that we only get values for the two countries that were included in the sample. If the mean cup points for each country is an important metric in our analysis, cluster sampling would be a bad idea.
```Python
coffee_ratings_top.groupby("country_of_origin")["total_cup_points"] \
	.mean()
>>country_of_origin
>>Brazil                   82.405909
>>Colombia                 83.106557
>>Guatemala                81.846575
>>Mexico                   80.890085
>>Taiwan                   82.001333
>>United States (Hawaii)   81.820411
>>Name: total_cup_points, dtype=float64

coffee_ratings_clust.groupby("country_of_origin")["total_cup_points"] \
	.mean()
>>country_of_origin
>>Colombia                 83.128904
>>Mexico                   80.936027
>>Name: total_cup_points, dtype=float64
```
## Let's practice!
Let's calculate some summary statistics.