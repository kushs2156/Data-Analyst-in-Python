One cool aspect of using an outer join is that, because it returns all rows from both merged tables and null where they do not match, you can use it to find rows that do not have a match in the other table. To try for yourself, you have been given two tables with a list of actors from two popular movies: _Iron Man 1_ and _Iron Man 2_. Most of the actors played in both movies. Use an outer join to find actors who **_did not_** act in both movies.

The _Iron Man 1_ table is called `iron_1_actors`, and _Iron Man 2_ table is called `iron_2_actors`. Both tables have been loaded for you and a few rows printed so you can see the structure.
![[Pasted image 20250128215153.png]]
- Save to `iron_1_and_2` the merge of `iron_1_actors` (left) with `iron_2_actors` tables with an outer join on the `id` column, and set suffixes to `('_1','_2')`.
- Create an index that returns `True` if `name_1` or `name_2` are null, and `False` otherwise.
```Python
# Merge iron_1_actors to iron_2_actors on id with outer join using suffixes
iron_1_and_2 = iron_1_actors.merge(iron_2_actors, how='outer',
                                   on='id',
                                   suffixes=('_1', '_2'))
                                     
# Create an index that returns true if name_1 or name_2 are null
m = ((iron_1_and_2['name_1'].isnull() == True) | 
     (iron_1_and_2['name_2'].isnull() == True))

# Print the first few rows of iron_1_and_2
print(iron_1_and_2[m].head())
```
