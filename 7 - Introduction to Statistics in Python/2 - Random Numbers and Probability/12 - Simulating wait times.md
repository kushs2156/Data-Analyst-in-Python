- Set the random seed to `334`.
- Import `uniform` from `scipy.stats`.
- Generate 1000 wait times from the continuous uniform distribution that models Amir's wait time. Save this as `wait_times`.
- Create a histogram of the simulated wait times and show the plot.
```Python
# Set random seed to 334
np.random.seed(334)

# Import uniform
from scipy.stats import uniform

# Generate 1000 wait times between 0 and 30 mins
wait_times = uniform.rvs(0, 30, size=1000)

print(wait_times)

# Create a histogram of simulated times and show plot
plt.hist(x=wait_times)
plt.show()
```
![[download 37.svg]]
