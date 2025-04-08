- Generate 5000 numbers from a uniform distribution, setting the parameters `low` to `-3` and `high` to `3`.
- Generate 5000 numbers from a normal distribution, setting the parameters `loc` to `5` and `scale` to `2`.
- Plot a histogram of `uniforms` with bins of width of `0.25` from `-3` to `3` using `plt.hist()`.
- Plot a histogram of `normals` with bins of width of `0.5` from `-2` to `13` using `plt.hist()`.
```Python
# Generate random numbers from a Uniform(-3, 3)
uniforms = np.random.uniform(low=-3, high=3, size=5000)

# Print uniforms
print(uniforms)

# Generate random numbers from a Normal(5, 2)
normals = np.random.normal(loc=5, scale=2, size=5000)

# Print normals
print(normals)

# Plot a histogram of uniform values, binwidth 0.25
plt.hist(uniforms, bins=np.arange(-3, 3.25, 0.25))
plt.show()

# Plot a histogram of normal values, binwidth 0.5
plt.hist(normals, bins=np.arange(-2, 13.5, 0.5))
plt.show()
```
![[download 1 5.svg]]
![[download 122.svg]]
