- Set the scale ("context") to `"paper"`, which is the smallest of the scale options.
```Python
# Set the context to "paper"
sns.set_context("paper")

# Create bar plot
sns.catplot(x="Number of Siblings", y="Feels Lonely",
            data=survey_data, kind="bar")

# Show plot
plt.show()
```
![[download 89.svg]]
- Change the context to `"notebook"` to increase the scale.
```Python
# Change the context to "notebook"
sns.set_context("notebook")

# Create bar plot
sns.catplot(x="Number of Siblings", y="Feels Lonely",
            data=survey_data, kind="bar")

# Show plot
plt.show()
```
![[download 90.svg]]
- Change the context to `"talk"` to increase the scale.
```Python
# Change the context to "talk"
sns.set_context("talk")

# Create bar plot
sns.catplot(x="Number of Siblings", y="Feels Lonely",
            data=survey_data, kind="bar")

# Show plot
plt.show()
```
![[download 91.svg]]

- Change the context to `"poster"`, which is the largest scale available.
```Python
# Change the context to "poster"
sns.set_context("poster")

# Create bar plot
sns.catplot(x="Number of Siblings", y="Feels Lonely",
            data=survey_data, kind="bar")

# Show plot
plt.show()
```
![[download 92.svg]]
