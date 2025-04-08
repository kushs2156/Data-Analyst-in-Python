- Select `weight_kilograms` and `late` from `late_shipments`, assigning the name `weight_vs_late`.
- Convert `weight_vs_late` from long-to-wide format, setting `columns` to `'late'`.
- Run a Wilcoxon-Mann-Whitney test for a difference in `weight_kilograms` when the shipment was late and on-time.
```Python
# Select the weight_kilograms and late columns
weight_vs_late = late_shipments[['weight_kilograms', 'late']]

# Convert weight_vs_late into wide format
weight_vs_late_wide = weight_vs_late.pivot(columns='late', 
                                           values='weight_kilograms')

# Run a two-sided Wilcoxon-Mann-Whitney test on weight_kilograms vs. late
wmw_test = pingouin.mwu(x=weight_vs_late_wide['Yes'], 
						y=weight_vs_late_wide['No'], 
						alternative='two-sided')

# Print the test results
print(wmw_test)
>>       U-val  alternative      p-val     RBC   CLES 
>>MWU  38145.0    two-sided  1.371e-05  -0.332  0.666
```