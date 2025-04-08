- Run a Kruskal-Wallis test on `weight_kilograms` between the different shipment modes in `late_shipments`.
```Python
# Run a Kruskal-Wallis test on weight_kilograms vs. shipment_mode
kw_test = pingouin.kruskal(data=late_shipments, 
						   dv='weight_kilograms', 
						   between='shipment_mode')

# Print the results
print(kw_test)
>>                Source  ddof1        H      p-unc 
>>Kruskal  shipment_mode      2  125.097  6.849e-28
```