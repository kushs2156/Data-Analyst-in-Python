One problem with stratified sampling is that we need to collect data from every subgroup. In cases where collecting data is expensive, for example, when we have to physically travel to a location to collect it, it can make our analysis prohibitively expensive. There's a cheaper alternative called cluster sampling.
## Stratified sampling vs. cluster sampling
The stratified sampling approach was to split the population into subgroups, then use simple random sampling on each of them. Cluster sampling means that we limit the number of subgroups in the analysis by picking a few of them with simple random sampling. We then perform simple random sampling on each subgroup as before.
## Varieties of coffee
Let's return to the coffee dataset and look at the varieties of coffee. In this image, each bean represents the whole subgroup rather than an individual coffee, and there are 28 of them. To extract unique varieties, we use the `.unique()` method. This returns an array, so wrapping it in the list function creates a list of unique varieties. 
```Python
varieties_pop = list(coffee_ratings['variety'].unique())
```
Let's suppose that it's expensive to work with all of the different varieties. Enter cluster sampling.
## Stage 1: sampling for subgroups
The first stage of cluster sampling is to randomly cut down the number of varieties, and we do this by randomly selecting them. Here, we've used the random.sample function from the random package to get three varieties, specified using the argument k.
```Python
import random
varieties_samp = random.sample(varieties_pop, k=3)
>>['Hawaiian Kona', 'Bourbon', 'SL28']
```
## Stage 2: sampling each group
The second stage of cluster sampling is to perform simple random sampling on each of the three varieties we randomly selected. We first filter the dataset for rows where the variety is one of the three selected, using the .isin method. 
```Python
variety_condition = coffee_ratings['variety'].isin(varieties_samp)
coffee_ratings_cluster = coffee_ratings[variety_condition]
```
To ensure that the isin filtering removes levels with zero rows, we apply the `cat.remove_unused_categories()` method on the Series of focus, which is variety here. If we exclude this method, we might receive an error when sampling by variety level. 
```Python
coffee_ratings_cluster['variety'] = 
	coffee_ratings_cluster['variety'].cat.remove_unused_categories()
```
The pandas code is the same as for stratified sampling. Here, we've opted for equal counts sampling, with five rows from each remaining variety.
```Python
coffee_ratings_cluster.groupby('variety') \ 
	.sample(n=5, random_state=2021)
```
Here's the first few columns of the result. Notice that there are the fifteen rows, which we'd expect from sampling five rows from three varieties.
## Multistage sampling
Note that we had two stages in the cluster sampling. We randomly sampled the subgroups to include, then we randomly sampled rows from those subgroups. Cluster sampling is a special case of multistage sampling. It's possible to use more than two stages. A common example is national surveys, which can include several levels of administrative regions, like states, counties, cities, and neighbourhoods.
## Let's practice!
Time to sample some clusters.