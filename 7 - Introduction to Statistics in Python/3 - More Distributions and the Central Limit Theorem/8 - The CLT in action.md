- Create a histogram of the `num_users` column of `amir_deals` and show the plot.
```Python
# Create a histogram of num_users and show
amir_deals['num_users'].hist()
plt.show()
```
![[download 40.svg]]
- Set the seed to `104`.
- Take a sample of size `20` with replacement from the `num_users` column of `amir_deals`, and take the mean.
```Python
# Set seed to 104
np.random.seed(104)

# Sample 20 num_users with replacement from amir_deals
samp_20 = amir_deals['num_users'].sample(20, replace=True)

# Take mean of samp_20
print(np.mean(samp_20))
```
- Repeat this 100 times using a `for` loop and store as `sample_means`. This will take 100 different samples and calculate the mean of each.
```Python
sample_means = []

# Loop 100 times
for i in range(100):
  # Take sample of 20 num_users
  samp_20 = amir_deals['num_users'].sample(20, replace=True)
  # Calculate mean of samp_20
  samp_20_mean = np.mean(samp_20)
  # Append samp_20_mean to sample_means
  sample_means.append(samp_20_mean)
print(sample_means)
```
- Convert `sample_means` into a `pd.Series`, create a histogram of the `sample_means`, and show the plot.
```Python
# Convert to Series and plot histogram
sample_means_series = pd.Series(sample_means)
sample_means_series.hist()

# Show plot
plt.show()
```
![[download 41.svg]]
