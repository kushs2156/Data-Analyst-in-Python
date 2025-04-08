- Calculate the standard deviation of `sampling_distribution_5`, `sampling_distribution_50`, and `sampling_distribution_500` (a standard deviation of sample means).
```Python
# Calculate the std. dev. of the mean attritions for each sampling distribution
sd_of_means_5 = np.std(sampling_distribution_5, ddof=1)
sd_of_means_50 = np.std(sampling_distribution_50, ddof=1)
sd_of_means_500 = np.std(sampling_distribution_500, ddof=1)

# Print the results
print(sd_of_means_5)
print(sd_of_means_50)
print(sd_of_means_500)
>>0.16602470961939433 
>>0.05050589317342329 
>>0.013451458572873713
```
How are the standard deviations of the sampling distributions related to the population standard deviation and the sample size?
- The standard deviation of the sampling distribution is approximately equal to the population standard deviation divided by the square root of the sample size.