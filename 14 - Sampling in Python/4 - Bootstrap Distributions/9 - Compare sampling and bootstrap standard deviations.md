Calculate the standard deviation of `popularity` in 4 ways.

- Population: from `spotify_population`, take the standard deviation of `popularity`.
- Original sample: from `spotify_sample`, take the standard deviation of `popularity`.
- Sampling distribution: from `sampling_distribution`, take its standard deviation and multiply by the square root of the sample size (`5000`).
- Bootstrap distribution: from `bootstrap_distribution`, take its standard deviation and multiply by the square root of the sample size.
```Python
# Calculate the population std dev popularity
pop_sd = spotify_population['popularity'].std(ddof=0)

# Calculate the original sample std dev popularity
samp_sd = spotify_sample['popularity'].std(ddof=1)

# Calculate the sampling dist'n estimate of std dev popularity
samp_distn_sd = np.std(sampling_distribution, ddof=1) * 
	np.sqrt(len(sampling_distribution))

# Calculate the bootstrap dist'n estimate of std dev popularity
boot_distn_sd = np.std(bootstrap_distribution, ddof=1) * 
	np.sqrt(len(bootstrap_distribution))

# Print the standard deviations
print([pop_sd, samp_sd, samp_distn_sd, boot_distn_sd])
>>[10.880065274257536, 10.85755549570291, 10.13269956909527, >>10.874815536126995]
```
Based on the four results you just calculated (`pop_sd`, `samp_sd`, `samp_distn_sd`, and `boot_distn_sd`), which statement is true?
- The calculation from the bootstrap distribution is the best estimate of the population standard deviation.