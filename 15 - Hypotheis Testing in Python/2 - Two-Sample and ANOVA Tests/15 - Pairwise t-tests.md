- Perform pairwise t-tests on `late_shipments`'s `pack_price` variable, grouped by `shipment_mode`, without doing any p-value adjustment.
```Python
# Perform a pairwise t-test on pack price, grouped by shipment mode
pairwise_results = pingouin.pairwise_tests(data=late_shipments, 
										   dv="pack_price", 
										   between="shipment_mode", 
										   padjust="none") 

# Print pairwise_results
print(pairwise_results)
```
- Modify the pairwise t-tests to use the Bonferroni p-value adjustment.
```Python
# Modify the pairwise t-tests to use Bonferroni p-value adjustment
pairwise_results = pingouin.pairwise_tests(data=late_shipments, 
                                           dv="pack_price",
                                           between="shipment_mode",
                                           padjust="bonf")
                                           
# Print pairwise_results
print(pairwise_results)
```
- Using the Bonferroni correction results and assuming a significance level of 0.1, for which pairs of shipment modes should you reject the null hypothesis that the pack prices are equal?
"Ocean" and "Air Charter"; "Ocean" and "Air"; "Air Charter" and "Air".
