There are several methods of sampling from a population. In this video, we'll look at simple random sampling and systematic random sampling.
## Simple random sampling
Simple random sampling works like a raffle or lottery. We start with our population of raffle tickets or lottery balls and randomly pick them out one at a time.

In our coffee ratings dataset, instead of raffle tickets or lottery balls, the population consists of coffee varieties. To perform simple random sampling, we take some at random, one at a time. Each coffee has the same chance as any other of being picked. When using this technique, sometimes we might end up with two coffees that were next to each other in the dataset, and sometimes we might end up with large areas of the dataset that were not selected from at all. We've already seen how to do simple random sampling with pandas. We call `.sample()` and set n to the size of the sample. We can also set the seed using the random_state argument to generate reproducible results, just like we did pseudo-random number generation. Previously, by not setting random_state when sampling, our code would generate a different random sample each time it was run.
```Python
coffee_ratings.sample(n=5, random_state=19000113)
```
## Systematic sampling
Another sampling method is known as systematic sampling. This samples the population at regular intervals. Here, looking from top to bottom and left to right within each row, every fifth coffee is sampled. Systematic sampling with pandas is slightly trickier than simple random sampling. The tricky part is determining how big the interval between each row should be for a given sample size. Suppose we want a sample size of five coffees. The population size is the number of rows in the whole dataset, and in this case, it's 1338. The interval is the population size divided by the sample size, but because we want the answer to be an integer, we perform integer division with two forward slashes. This is like standard division but discards any fractional part. 
```Python
sample_size = 5
pop_size = len(coffee_ratings)
print(pop_size)
>>1338

interval = pop_size // sample_size
print(interval)
>>267
```
1338 divided by 5 is actually 267.6, and discarding the fractional part leaves 267. Thus, to get a systematic sample of five coffees, we will select every 267th coffee in the dataset.

To select every 267th row, we call `.iloc[]` on coffee_ratings and pass double-colons and the interval, which is 267 in this case. Double-colon interval tells pandas to select every two hundred and sixty-seventh row from zero to the end of the DataFrame.
```Python
coffee_ratings.iloc[::267]
```
## The trouble with systematic sampling
There is a problem with systematic sampling, though. Suppose we are interested in statistics about the aftertaste attribute of the coffees. To examine this, first, we use `reset_index()` to create a column of index values in our DataFrame that we can plot. Plotting aftertaste against index shows a pattern. Earlier rows generally have higher aftertaste scores than later rows. This introduces bias into the statistics that we calculate. In general, it is only safe to use systematic sampling if a plot like this has no pattern; that is, it just looks like noise.
```Python
coffee_ratings_with_id = coffee_ratings.reset_index()
coffee_ratings_with_id.plot(x="index", y="aftertaste", kind="scatter")
plt.show()
```
## Making systematic sampling safe
To ensure that systematic sampling is safe, we can randomise the row order before sampling. .sample has an argument named frac that lets us specify the proportion of the dataset to return in the sample, rather than the absolute number of rows that n specifies. Setting frac to one randomly samples the whole dataset. In effect, this randomly shuffles the rows. Next, the indices need to be reset so that they go in order from zero again. Specifying drop equals True clears the previous row indexes, and chaining to another reset_index call creates a column containing these new indexes. 
```Python
shuffled = coffee.ratings.sample(frac=1)
shuffled = shuffled.reset_index(drop=True).reset_index()
```
Redrawing the plot with the shuffled dataset shows no pattern between aftertaste and index. This is great, but note that once we've shuffled the rows, systematic sampling is essentially the same as simple random sampling.
## Let's practice!
Let's get sampling!