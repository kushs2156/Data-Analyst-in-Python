- Group `late_shipments` by `shipment_mode` and calculate the mean `pack_price` for each group, storing the result in `xbar_pack_by_mode`.
- Group `late_shipments` by `shipment_mode` and calculate the standard deviation `pack_price` for each group, storing the result in `s_pack_by_mode`.
- Create a boxplot from `late_shipments` with `"pack_price"` as `x` and `"shipment_mode"` as `y`.
```Python
# Calculate the mean pack_price for each shipment_mode
xbar_pack_by_mode = late_shipments.groupby('shipment_mode')\
	['pack_price'].mean()

# Print the grouped means
print(xbar_pack_by_mode)

# Calculate the standard deviation of the pack_price for each shipment_mode
s_pack_by_mode = late_shipments.groupby('shipment_mode')\
['pack_price'].std()

# Print the grouped standard deviations
print(s_pack_by_mode)

# Boxplot of shipment_mode vs. pack_price
sns.boxplot(x="pack_price", y="shipment_mode", data=late_shipments)
plt.show()
```
![[download 132.svg]]
