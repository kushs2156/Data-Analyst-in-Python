- Create a scatter plot with `nb_sold` on the x-axis and `avg_price` on the y-axis. Title it `"Number of avocados sold vs. average price"`.
- Show the plot.
```Python
# Scatter plot of avg_price vs. nb_sold with title
avocados.plot(x="nb_sold", y="avg_price", kind="scatter",
			  title="Number of avocados sold vs. average price")

# Show the plot
plt.show()
```
![[download 1 1.svg]]

