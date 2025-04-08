- Add a new column to `homelessness`, named `total`, containing the sum of the `individuals` and `family_members` columns.
- Add another column to `homelessness`, named `p_homeless`, containing the proportion of the `total` homeless population to the total population in each state `state_pop`.
```Python
# Add total col as sum of individuals and family_members
homelessness["total"] = homelessness["individuals"] + homelessness["family_members"]

# Add p_homeless col as proportion of total homeless population to the state population
homelessness["p_homeless"] = homelessness["total"] / homelessness["state_pop"]

# See the result
print(homelessness)
```
