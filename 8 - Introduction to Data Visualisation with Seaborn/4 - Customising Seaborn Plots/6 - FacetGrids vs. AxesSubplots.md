- Identify what type of object plot `g` is and assign it to the variable `type_of_g`.
```Python
# Create scatter plot
g = sns.relplot(x="weight", 
                y="horsepower", 
                data=mpg,
                kind="scatter")

# Identify plot type
type_of_g = type(g)

# Print type
print(type_of_g)
>><class 'seaborn.axisgrid.FacetGrid'>
```
We've just seen that `sns.relplot()` creates FacetGrid objects. Which other Seaborn function creates a FacetGrid object instead of an AxesSubplot object?
- `sns.catplot()`