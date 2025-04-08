- Replicate the provided code so that it runs `500` times. Assign the resulting list of sample means to `mean_attritions`.
- Draw a histogram of the `mean_attritions` list with 16 bins.
```Python
# Create an empty list
mean_attritions = []
# Loop 500 times to create 500 sample means
for i in range(500):
    mean_attritions.append(
        attrition_pop.sample(n=60)['Attrition'].mean()
    )
# Print out the first few entries of the list
print(mean_attritions[0:5])

# Create a histogram of the 500 sample means
plt.hist(mean_attritions, bins=16)
plt.show()
```
![[download 127.svg]]