- Get the count of each value in the `freight_cost_group` column of `late_shipments`.
- Insert a suitable number to inspect whether the counts are "big enough" for a two sample t-test.
```Python
# Count the freight_cost_group values
counts = late_shipments['freight_cost_group'].value_counts()

# Print the result
print(counts)

# Inspect whether the counts are big enough
print((counts >= 30).all())
```
- Get the count of each value in the `late` column of `late_shipments`.
- Insert a suitable number to inspect whether the counts are "big enough" for a one sample proportion test.
```Python
# Count the late values
counts = late_shipments['late'].value_counts()

# Print the result
print(counts)

# Inspect whether the counts are big enough
print((counts >= 10).all())
```
- Get the count of each value in the `freight_cost_group` column of `late_shipments` grouped by `vendor_inco_term`.
- Insert a suitable number to inspect whether the counts are "big enough" for a chi-square independence test.
```Python
# Count the values of freight_cost_group grouped by vendor_inco_term
counts = late_shipments.groupby('vendor_inco_term')\
						['freight_cost_group'].value_counts()

# Print the result
print(counts)

# Inspect whether the counts are big enough
print((counts >= 5).all())
```
- Get the count of each value in the `shipment_mode` column of `late_shipments`.
- Insert a suitable number to inspect whether the counts are "big enough" for an ANOVA test.
```Python
# Count the shipment_mode values
counts = late_shipments['shipment_mode'].value_counts()

# Print the result
print(counts)

# Inspect whether the counts are big enough
print((counts >= 30).all())
```