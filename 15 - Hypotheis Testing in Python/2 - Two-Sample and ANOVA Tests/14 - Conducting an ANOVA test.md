- Run an ANOVA on `late_shipments` investigating `'pack_price'` (the dependent variable) between the groups of `'shipment_mode'`.
```Python
# Run an ANOVA for pack_price across shipment_mode
anova_results = pingouin.anova(data=late_shipments, 
				dv="pack_price", between="shipment_mode")

# Print anova_results
print(anova_results)
>>          Source  ddof1  ddof2       F      p-unc    np2 
>>0  shipment_mode      2    997  21.865  5.089e-10  0.042
```
- Assuming a significance level of 0.1, should you reject the null hypothesis that there is no difference in pack prices between shipment modes?
Yes. The p-value is less than or equal to the significance level, so the null hypothesis should be rejected.