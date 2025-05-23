- Merge `movie_to_genres` and `pop_movies` using a right join. Save the results as `genres_movies`.
- Group `genres_movies` by `genre` and count the number of `id` values.
```Python
# Use right join to merge the movie_to_genres and pop_movies tables
genres_movies = movie_to_genres.merge(pop_movies, how='right', 
								left_on='movie_id', right_on='id')

# Count the number of genres
genre_count = genres_movies.groupby('genre').agg({'id':'count'})

# Plot a bar chart of the genre_count
genre_count.plot(kind='bar')
plt.show()
```
![[download 25.svg]]
