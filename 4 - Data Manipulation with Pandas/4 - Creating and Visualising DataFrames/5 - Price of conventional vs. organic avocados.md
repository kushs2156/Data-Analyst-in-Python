- Subset `avocados` for the `"conventional"` `type` and create a histogram of the `avg_price` column.
- Create a histogram of `avg_price` for `"organic"` `type` avocados.
- Add a legend to your plot, with the names `"conventional"` and `"organic"`.
- Show your plot.
```Python
# Histogram of conventional avg_price 
avocados[avocados["type"] == "conventional"]["avg_price"].hist()

# Histogram of organic avg_price
avocados[avocados["type"] == "organic"]["avg_price"].hist()

# Add a legend
plt.legend(["conventional", "organic"])

# Show the plot
plt.show()
```
![[download 23.svg]]
- Modify your code to adjust the transparency of both histograms to `0.5` to see how much overlap there is between the two distributions.
```Python
# Modify histogram transparency to 0.5 
avocados[avocados["type"] == "conventional"]["avg_price"].hist(alpha=0.5)

# Modify histogram transparency to 0.5
avocados[avocados["type"] == "organic"]["avg_price"].hist(alpha=0.5)

# Add a legend
plt.legend(["conventional", "organic"])

# Show the plot
plt.show()
```
![[download 1 2.svg]]
- Modify your code to use 20 bins in both histograms.
```Python
# Modify bins to 20
avocados[avocados["type"] == "conventional"]["avg_price"].hist(alpha=0.5, bins=20)

# Modify bins to 20
avocados[avocados["type"] == "organic"]["avg_price"].hist(alpha=0.5, bins=20)

# Add a legend
plt.legend(["conventional", "organic"])

# Show the plot
plt.show()
```
![[download 2 1.svg]]

