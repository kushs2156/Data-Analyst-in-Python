- Calculate the numerator of the t test statistic.
- Calculate the denominator of the t test statistic.
- Use those two numbers to calculate the t test statistic.
```Python
# Calculate the numerator of the test statistic
numerator = xbar_no - xbar_yes

# Calculate the denominator of the test statistic
denominator = np.sqrt((s_no ** 2/n_no + s_yes ** 2/n_yes))

# Calculate the test statistic
t_stat = numerator / denominator

# Print the test statistic
print(t_stat)
>>-2.3936661778766433
```