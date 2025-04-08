- Find the total number of rows in `late_shipments`.
- Add a column named `n` to the `hypothesized` DataFrame that is the `hypothesized` `prop` column times `n_total`.
- Create a bar graph of `'n'` versus `'vendor_inco_term'` for the `incoterm_counts` data, specifying a red colour.
- Add blue bars to the plot showing the same results from the `hypothesized` DataFrame, specifying an `alpha` of `0.5`.
```Python
# Find the number of rows in late_shipments
n_total = len(late_shipments)

# Print n_total
print(n_total)
>>999

# Create n column that is prop column * n_total
hypothesized['n'] = hypothesized['prop'] * n_total

# Print the modified hypothesized DataFrame
print(hypothesized)

# Plot a red bar graph of n vs. vendor_inco_term for incoterm_counts
plt.bar(incoterm_counts['vendor_inco_term'], incoterm_counts['n'], 
		color='red', label="Observed")
plt.legend()
plt.show()

# Add a blue bar plot for the hypothesized counts
plt.bar(hypothesized['vendor_inco_term'], hypothesized['n'], 
		color='blue', alpha=0.5, label="Hypothesized")
plt.legend()
plt.show()
```
![[download 134.svg]]
![[download 135.svg]]
