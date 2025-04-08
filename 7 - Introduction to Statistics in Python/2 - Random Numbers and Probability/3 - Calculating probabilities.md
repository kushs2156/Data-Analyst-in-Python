- Count the number of deals Amir worked on for each `product` type using `.value_counts()` and store in `counts`.
- Calculate the probability of selecting a deal for the different product types by dividing the counts by the total number of deals Amir worked on. Save this as `probs`.
```Python
# Count the deals for each product
counts = amir_deals['product'].value_counts()

print(counts)

# Calculate probability of picking a deal with each product
probs = counts / counts.sum()

print(probs)
```
If you randomly select one of Amir's deals, what's the probability that the deal will involve `Product C`?
- 8.43%