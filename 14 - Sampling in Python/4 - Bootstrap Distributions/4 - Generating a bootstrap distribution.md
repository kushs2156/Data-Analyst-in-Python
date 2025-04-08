- Generate a single bootstrap resample from `spotify_sample`.
- Calculate the mean of the `danceability` column of `spotify_1_resample` using `numpy`.
```Python
# Generate 1 bootstrap resample
spotify_1_resample = spotify_sample.sample(frac=1, replace=True)

# Print the resample
print(spotify_1_resample)

# Calculate of the danceability column of spotify_1_resample
mean_danceability_1 = np.mean(spotify_1_resample['danceability'])

# Print the result
print(mean_danceability_1)
>>0.5910226305934319
```
- Replicate the expression provided 1000 times.
- Create a bootstrap distribution by drawing a histogram of `mean_danceability_1000`.
```Python
# Replicate this 1000 times
mean_danceability_1000 = []
for i in range(1000):
    mean_danceability_1000.append(
        np.mean(spotify_sample.sample(frac=1, replace=True)\
        ['danceability'])
    )
    
# Print the result
print(mean_danceability_1000)

# Draw a histogram of the resample means
plt.hist(mean_danceability_1000)
plt.show()
```
![[download 130.svg]]
