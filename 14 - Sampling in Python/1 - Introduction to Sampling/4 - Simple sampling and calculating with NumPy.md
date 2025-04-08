- Create a `pandas` Series, `loudness_pop`, by subsetting the `loudness` column from `spotify_population`.
- Sample `loudness_pop` to get 100 random values, assigning to `loudness_samp`.
- Calculate the mean of `loudness_pop` using `numpy`.
- Calculate the mean of `loudness_samp` using `numpy`.
```Python
# Create a pandas Series from the loudness column of spotify_population
loudness_pop = spotify_population['loudness']

# Sample 100 values of loudness_pop
loudness_samp = loudness_pop.sample(n=100)

print(loudness_samp)

# Calculate the mean of loudness_pop
mean_loudness_pop = np.mean(loudness_pop)

# Calculate the mean of loudness_samp
mean_loudness_samp = np.mean(loudness_samp)

print(mean_loudness_pop)
print(mean_loudness_samp)
```
