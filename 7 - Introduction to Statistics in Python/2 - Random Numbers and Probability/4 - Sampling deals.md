- Set the random seed to `24`.
- Take a sample of `5` deals **without** replacement and store them as `sample_without_replacement`.
- Take a sample of 5 deals **with** replacement and save as `sample_with_replacement`.
```Python
# Set random seed
np.random.seed(24)

# Sample 5 deals without replacement
sample_without_replacement = amir_deals.sample(5, replace = False)
print(sample_without_replacement)

# Sample 5 deals with replacement
sample_with_replacement = amir_deals.sample(5, replace = True)
print(sample_with_replacement)
```
What type of sampling is better to use for this situation?
- Without replacement