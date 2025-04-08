- Add an index column to `attrition_pop`, assigning the result to `attrition_pop_id`.
- Create a scatter plot of `YearsAtCompany` versus `index` for `attrition_pop_id` using pandas `.plot()`.
```Python
# Add an index column to attrition_pop
attrition_pop_id = attrition_pop.reset_index()

# Plot YearsAtCompany vs. index for attrition_pop_id
attrition_pop_id.plot(x="index", y="YearsAtCompany", kind="scatter")
plt.show()
```
![[download 123.svg]]
- Randomly shuffle the rows of `attrition_pop`.
- Reset the row indexes, and add an index column to `attrition_pop`.
- Repeat the scatter plot of `YearsAtCompany` versus `index`, this time using `attrition_shuffled`.
```Python
# Shuffle the rows of attrition_pop
attrition_shuffled = attrition_pop.sample(frac=1) 

# Reset the row indexes and create an index column
attrition_shuffled = attrition_shuffled.reset_index(drop=True) \ 
						.reset_index()

# Plot YearsAtCompany vs. index for attrition_shuffled
attrition_shuffled.plot(x="index", y="YearsAtCompany", kind="scatter")
plt.show()
```
![[download 124.svg]]
Does a systematic sample always produce a sample similar to a simple random sample?
- No. This is not true if the data is sorted in some way.