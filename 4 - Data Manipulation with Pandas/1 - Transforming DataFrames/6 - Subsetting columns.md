- Create a Series called `individuals` that contains only the `individuals` column of `homelessness`.
- Create a DataFrame called `state_fam` that contains only the `state` and `family_members` columns of `homelessness`, in that order.
- Create a DataFrame called `ind_state` that contains the `individuals` and `state` columns of `homelessness`, in that order.
```Python
# Select the individuals column
individuals = homelessness["individuals"]

print(individuals.head())

# Select the state and family_members columns
state_fam = homelessness[["state", "family_members"]]

print(state_fam.head())

# Select only the individuals and state columns, in that order
ind_state = homelessness[["individuals", "state"]]

print(ind_state.head())
```
