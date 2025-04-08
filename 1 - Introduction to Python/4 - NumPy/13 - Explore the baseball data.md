- The code to print out the mean height is already included. Complete the code for the median height. Replace `None` with the correct code.
- Use `np.std()` on the first column of `np_baseball` to calculate `stddev`. Replace `None` with the correct code.
- Do big players tend to be heavier? Use `np.corrcoef()` to store the correlation between the first and second column of `np_baseball` in `corr`. Replace `None` with the correct code.
```Python
avg = np.mean(np_baseball[:,0])
print("Average: " + str(avg))
>>Average: 73.6896551724138

# Print median height
med = np.median(np_baseball[:,0])
print("Median: " + str(med))
>>Median: 74.0

# Print out the standard deviation on height
stddev = np.std(np_baseball[:,0])
print("Standard Deviation: " + str(stddev))
>>Standard Deviation: 2.312791881046546

# Print out correlation between first and second column
corr = np.corrcoef(np_baseball[:,0], np_baseball[:,1])
print("Correlation: " + str(corr))
>>Correlation: [[1. 0.53153932 ] 
>>              [0.53153932 1. ]]
```