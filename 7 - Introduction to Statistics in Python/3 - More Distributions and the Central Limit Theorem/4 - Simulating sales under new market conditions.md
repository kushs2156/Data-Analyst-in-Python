- Currently, Amir's average sale amount is $5000. Calculate what his new average amount will be if it increases by 20% and store this in `new_mean`.
- Amir's current standard deviation is $2000. Calculate what his new standard deviation will be if it increases by 30% and store this in `new_sd`.
- Create a variable called `new_sales`, which contains 36 simulated amounts from a normal distribution with a mean of `new_mean` and a standard deviation of `new_sd`.
- Plot the distribution of the `new_sales` `amount`s using a histogram and show the plot.
```Python
# Calculate new average amount
new_mean = 5000 * 1.20

# Calculate new standard deviation
new_sd = 2000 * 1.30

# Simulate 36 new sales
new_sales = norm.rvs(new_mean, new_sd, size=36)

# Create histogram and show
plt.hist(x=new_sales)
plt.show()
```
![[download 39.svg]]
