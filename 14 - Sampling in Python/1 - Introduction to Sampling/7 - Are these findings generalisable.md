- Plot a histogram of `duration_minutes` from `spotify_population` with bins of width `0.5` from `0` to `15` using pandas `.hist()`.
```Python
# Visualize the distribution of duration_minutes as a histogram
spotify_population['duration_minutes'].hist( \ 
				bins=np.arange(0,15.5, 0.5))
plt.show()
```
![[download 120.svg]]
- Update the histogram code to use the `spotify_mysterious_sample2` dataset.
```Python
# Update the histogram to use spotify_mysterious_sample2
spotify_mysterious_sample2['duration_minutes'].hist( \ 
				bins=np.arange(0, 15.5, 0.5))
plt.show()
```
![[download 121.svg]]
_Compare the two histograms you drew._ Are the duration values in the sample generalisable to the general population?
- Yes. The sample selected is likely a random sample of all songs in the population.