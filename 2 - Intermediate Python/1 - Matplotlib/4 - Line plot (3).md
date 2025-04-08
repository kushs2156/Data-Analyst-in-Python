- Print the last item from both the list `gdp_cap`, and the list `life_exp`; it is information about Zimbabwe.
- Build a line chart, with `gdp_cap` on the x-axis, and `life_exp` on the y-axis. Does it make sense to plot this data on a line plot?
- Don't forget to finish off with a `plt.show()` command, to actually display the plot.
```Python
# Print the last item of gdp_cap and life_exp
print(gdp_cap[-1])
print(life_exp[-1])
>>469.70929810000007 
>>43.487

# Make a line plot, gdp_cap on the x-axis, life_exp on the y-axis
plt.plot(gdp_cap, life_exp)

# Display the plot
plt.show()
```
![[download 4.svg]]
