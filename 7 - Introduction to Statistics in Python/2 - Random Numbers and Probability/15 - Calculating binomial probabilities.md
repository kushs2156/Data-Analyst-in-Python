- What's the probability that Amir closes all 3 deals in a week? Save this as `prob_3`.
```Python
# Probability of closing 3 out of 3 deals
prob_3 = binom.pmf(3, 3, 0.3)

print(prob_3)
```
- What's the probability that Amir closes 1 or fewer deals in a week? Save this as `prob_less_than_or_equal_1`.
```Python
# Probability of closing <= 1 deal out of 3 deals
prob_less_than_or_equal_1 = binom.cdf(1, 3, 0.3)

print(prob_less_than_or_equal_1)
```
- What's the probability that Amir closes more than 1 deal? Save this as `prob_greater_than_1`.
```Python
prob_less_than_or_equal_1 = 1 - binom.cdf(1, 3, 0.3)

print(prob_less_than_or_equal_1)
```