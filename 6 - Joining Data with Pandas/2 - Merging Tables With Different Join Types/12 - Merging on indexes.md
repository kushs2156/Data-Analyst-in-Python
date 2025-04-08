So far, we've only looked at merging two tables together using their columns. In this lesson, we'll discuss how to merge tables using their indexes. Often, the DataFrame indexes are given a unique id that we can use when merging two tables together.
## Table with an Index
Here, we show the movies table that was introduced earlier in this chapter. The index is the default 0, 1, 2, 3, etc., auto-increment. In this second version, the id column is the index for the table. There are different methods to set the index of a table, but if our data starts off in a CSV file, we can use the `index_col` argument of the read_csv method. 
```Python
movies = pd.read_csv('tmdb_movies.csv', index_col=['id'])
```
This lesson will not focus on how to set a table index, but how to use that index to merge two tables together.
## Merge Index datasets
Recall our example to merge the movies and taglines tables using the id column with a left join. Let's recreate that merge using the index which is now the id for tables. Our merge statement looks identical to before. However, in this case we are inputting to the 'on' argument the index level name which is called 'id'. The merge method automatically adjusts to accept index names or column names. The returned table looks as before, except the 'id' is the index.
```Python
movies_taglines = movies.merge(taglines, on='id', how='left')
```
## MultiIndex datasets
Let's try a multiIndex merge. Here, we have two tables with a multiIndex that holds the movie ID and cast ID. The first table, named 'samuel', has the movie and cast ID for a group of movies that Samuel L. Jackson acted in. The second table, named cast, has the movie ID and cast ID for a number of movie characters. Let's merge these two tables on their multiIndex.
```Python
samuel = pd.read_csv('samuel.csv', index_col=['movie_id', 'cast_id'])

casts = pd.read_csv('casts.csv', index_col=['movie_id', 'cast_id'])
```
In this merge, we pass in a list of index level names to the 'on' argument, just like we did when merging on multiple columns. Since this is an inner join, both the movie_id and cast_id must match in each table to be returned in the result. It's interesting to see that Samuel Jackson has acted in over 65 movies! That's a lot.
```Python
samuel_casts = samuel.merge(casts, on=['movie_id', 'cast_id'])
```
## Index merge with left_on and right_on
There is one more thing regarding merging on indexes. If the index level names are different between the two tables that we want to merge, then we can use the left_on and right_on arguments of the merge method. Let's go back to our movies table, shown in the top panel, and merge it with our movies_to_genres table, shown in the lower panel.
```Python
movies_genres = movies.merge(movies_to_genres, left_on='id',
							 left_index=True, right_on='movie_id',
							 right_index=True)
```
In this merge, since we list the movies table as the left table, we set `left_on='id'` and `right_on='movie_id'`. Additionally, since we are merging on indexes, we need to set left_index and right_index to True. These arguments take only True or False. Whenever we are using the left_on or right_on arguments with an index, we need to set the respective left_index and right_index arguments to True. The left_index and right_index tell the merge method to use the separate indexes.
## Let's practice!
Now it's time for you try out a few exercises.