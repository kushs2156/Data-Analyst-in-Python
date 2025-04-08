- Merge the `movies` and `ratings` tables on the `id` column, keeping all rows from the `movies` table, and save the result as `movies_ratings`.
```Python
# Merge to the movies table the ratings table on the index
movies_ratings = movies.merge(ratings, on='id', how='left')

# Print the first few rows of movies_ratings
print(movies_ratings.head())
```
