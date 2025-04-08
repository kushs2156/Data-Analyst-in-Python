Calculate the mean `popularity` in 4 ways:

- Population: from `spotify_population`, take the mean of `popularity`.
- Sample: from `spotify_sample`, take the mean of `popularity`.
- Sampling distribution: from `sampling_distribution`, take its mean.
- Bootstrap distribution: from `bootstrap_distribution`, take its mean.
```Python
# Calculate the population mean popularity
pop_mean = spotify_population['popularity'].mean()

# Calculate the original sample mean popularity
samp_mean = spotify_sample['popularity'].mean()

# Calculate the sampling dist'n estimate of mean popularity
samp_distn_mean = np.mean(sampling_distribution)

# Calculate the bootstrap dist'n estimate of mean popularity
boot_distn_mean = np.mean(bootstrap_distribution)

# Print the means
print([pop_mean, samp_mean, samp_distn_mean, boot_distn_mean])
>>[54.837142308430955, 54.8686, 54.83586444000001, 54.86607339999999]
```
Based on the four means you just calculated (`pop_mean`, `samp_mean`, `samp_distn_mean`, and `boot_distn_mean`), which statement is true?
- The sampling distribution mean is the best estimate of the true population mean; the bootstrap distribution mean is closest to the original sample mean.
