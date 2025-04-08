- Calculate the mean of `sampling_distribution_5`, `sampling_distribution_50`, and `sampling_distribution_500` (a mean of sample means).
```Python
# Calculate the mean of the mean attritions for each sampling distribution
mean_of_means_5 = np.mean(sampling_distribution_5)
mean_of_means_50 = np.mean(sampling_distribution_50)
mean_of_means_500 = np.mean(sampling_distribution_500)

# Print the results
print(mean_of_means_5)
print(mean_of_means_50)
print(mean_of_means_500)
>>0.16560000000000002 
>>0.16416000000000003 
>>0.16119799999999998
```
How does sample size affect the mean of the sample means?
- Regardless of sample size, the mean of the sampling distribution is a close approximation to the population mean.