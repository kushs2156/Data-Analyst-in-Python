- Create a histogram of the `group_size` column of `restaurant_groups`, setting `bins` to `[2, 3, 4, 5, 6]`. Remember to show the plot.
```Python
# Create a histogram of restaurant_groups and show plot
restaurant_groups['group_size'].hist(bins=np.linspace(2,6,5))
plt.show()
```
![[download 36.svg]]
- Count the number of each `group_size` in `restaurant_groups`, then divide by the number of rows in `restaurant_groups` to calculate the probability of randomly selecting a group of each size. Save as `size_dist`.
- Reset the index of `size_dist`.
- Rename the columns of `size_dist` to `group_size` and `prob`.
```Python
# Create probability distribution
size_dist = restaurant_groups['group_id'] / restaurant_groups.count()

# Reset index and rename columns
size_dist = size_dist.reset_index()
size_dist.columns = ['group_size', 'prob']

print(size_dist)
```
- Calculate the expected value of the `size_dist`, which represents the expected group size, by multiplying the `group_size` by the `prob` and taking the sum.
```Python
# Calculate expected value
expected_value = np.sum(size_dist['group_size'] * size_dist['prob'])
print(expected_value)
```
- Calculate the probability of randomly picking a group of 4 or more people by subsetting for groups of size 4 or more and summing the probabilities of selecting those groups.
```Python
# Subset groups of size 4 or more
groups_4_or_more = size_dist['group_size'] >= 4

# Sum the probabilities of groups_4_or_more
prob_4_or_more = size_dist[groups_4_or_more]['prob'].sum()
print(prob_4_or_more)
```