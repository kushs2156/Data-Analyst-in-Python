- Define a Series of Booleans describing whether or not each `continent` is outside of `Oceania`; call this Series `not_oceania`.
```Python
# Define a Series describing whether each continent is outside of Oceania
not_oceania = ~unemployment["continent"].isin(["Oceania"])
```
- Use Boolean indexing to print the `unemployment` DataFrame without any of the data related to countries in Oceania.
```Python
# Print unemployment without records related to countries in Oceania
print(unemployment[not_oceania])
```
