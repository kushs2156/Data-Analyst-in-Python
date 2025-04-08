- Plot a histogram of the `acousticness` from `spotify_population` with bins of width `0.01` from `0` to `1` using pandas `.hist()`.
```Python
# Visualize the distribution of acousticness with a histogram
spotify_population['acousticness'].hist(bins=np.arange(0, 1.01, 0.01))
plt.show()
```
![[download 118.svg]]
- Update the histogram code to use the `spotify_mysterious_sample` dataset.
```Python
# Update the histogram to use spotify_mysterious_sample
spotify_mysterious_sample['acousticness'].hist( \ 
					bins=np.arange(0, 1.01, 0.01))
plt.show()
```
![[download 119.svg]]
_Compare the two histograms you drew._ Are the `acousticness` values in the sample generalisable to the general population?
- No. The `acousticness` samples are consistently higher than those in the general population.