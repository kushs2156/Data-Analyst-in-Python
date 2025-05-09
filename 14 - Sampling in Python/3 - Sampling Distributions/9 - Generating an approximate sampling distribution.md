- Sample one to eight, five times, with replacement. Assign to `five_rolls`.
- Calculate the mean of `five_rolls`.
```Python
# Sample one to eight, five times, with replacement
five_rolls = np.random.choice(list(range(1, 9)), size=5, replace=True)

# Print the mean of five_rolls
print(five_rolls.mean())
```
- Replicate the sampling code 1000 times, assigning each result to the list `sample_means_1000`.
- Plot `sample_means_1000` as a histogram with `20` bins.
```Python
# Replicate the sampling code 1000 times
sample_means_1000 = []
for i in range(1000):
    sample_means_1000.append(
        np.random.choice(list(range(1, 9)),size=5,replace=True).mean()
    )
# Print the first 10 entries of the result
print(sample_means_1000[0:10])

# Draw a histogram of sample_means_1000 with 20 bins
plt.hist(sample_means_1000, bins=20)
plt.show()
```
![[download 129.svg]]
