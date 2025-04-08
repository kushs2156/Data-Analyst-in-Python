All right, let's continue on. You now know how to use the merge method to perform an inner and left join. The merge method supports two other join types.
## Right join
Let's start with the right join. It will return all of the rows from the right table and includes only those rows from the left table that have matching values. It is the mirror opposite of the left join. These example tables show the result of a right join. Only rows from the left table where the column C matches are returned. Where there isn't a match, the columns from the left table will be missing in the result table, like rows one and four.
## Looking at data
For this lesson, let's look at another table called movie_to_genres. Movies can have multiple genres, and this table lists different genres for each movie.
```Python
movie_to_genres = pd.read_csv('tmdb_movie_to_genres.csv')
tv_genre = movie_to_genres[movie_to_genres['genre'] == 'TV Movie']
```
For our right join example, let's take a sample of this data subsetting to develop a table of movies from the TV Movie genre.
## Data to merge
Our goal is to merge it with the movies table. We will set movies as our left table and merge it with the tv_genre table. We want to use a right join to check that our movies table is not missing data. In addition to showing a right join, this example also allows us to look at another feature. Notice that the column with the movie ID number in the movies table is named `id`, and in the tv_genre table it is named `movie_id`. The merge method has a feature to take this into account.

The code for this merge has some new elements. First of all, we set the how argument to right so that the merge performs a right join. Additionally, we introduce two new arguments, named `left_on` and `right_on`. They allow us to tell the merge which key columns from each table to merge the tables. We list movies as the left table, so we set left_on to id and right_on to movie_id. 
```Python
tv_movies = movies.merge(tv_genre, how='right',
						 left_on='id', right_on='movie_id')
```
Our returned table has movies that match our table of tv_genres. There does not appear to be any null values in the columns from the movies table. We could explore further. However, let's move on to our last type of join.
## Outer join
Our last type of join is called an outer join. An outer join will return all of the rows from both tables regardless if there is a match between the tables. Here is a simple example of an outer join. Where the key column used to join the tables has no match, null values are returned. That is why in the result, the columns from the left table are missing in rows one and five, and in column D row three is missing. For an example of this, we filter the movie_to_genres table as before into two very small tables. One table has data on Family movies, and the other has Comedy movies.

In this merge, we list the family table as the left table and merge it on the movie_id column. The how argument is set to outer for an outer join. Both of our tables have the same column names. Therefore, we add suffixes to show what table the columns originated. 
```Python
family_comedy = family.merge(comedy, how='outer',
							 suffixes=('_fam', '_com'))
```
In our result table, every row is returned for both tables and we see some null values. In our original comedy tables ID number 12 does not exist. Therefore a null is shown. Similarly, in our last row, movie ID 13 wasn't in the family dataset so it has a null.
## Let's practice!
Let's practice!