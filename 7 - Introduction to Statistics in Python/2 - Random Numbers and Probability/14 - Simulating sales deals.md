- Import `binom` from `scipy.stats` and set the random seed to 10.
- Simulate 1 deal worked on by Amir, who wins 30% of the deals he works on.
- Simulate a typical week of Amir's deals, or one week of 3 deals.
- Simulate a year's worth of Amir's deals, or 52 weeks of 3 deals each, and store in `deals`.
- Print the mean number of deals he won per week.
```Python
# Import binom from scipy.stats
from scipy.stats import binom

# Set random seed to 10
np.random.seed(10)

# Simulate a single deal
print(binom.rvs(1, 0.3, size=1))

# Simulate 1 week of 3 deals
print(binom.rvs(3, 0.3, size=1))

# Simulate 52 weeks of 3 deals
deals = binom.rvs(3, 0.3, size=52)

# Print mean deals won per week
print(deals.sum() / 52)
>>0.8269230769230769
```