- Filter `homelessness` for cases where the USA census `state` is in the list of Mojave states, `canu`, assigning to `mojave_homelessness`. _View the printed result._
```Python
# The Mojave Desert states
canu = ["California", "Arizona", "Nevada", "Utah"]

# Filter for rows in the Mojave Desert states
mojave_homelessness = homelessness[homelessness["state"].isin(canu)]

# See the result
print(mojave_homelessness)
```
