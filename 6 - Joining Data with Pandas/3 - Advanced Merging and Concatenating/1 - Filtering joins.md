Welcome to the third chapter! In this lesson, we will discuss a type of join called a filtering join. pandas doesn't provide direct support for filtering joins, but we will learn how to replicate them.

## Mutating versus filtering joins
So far, we have only worked with mutating joins, which combines data from two tables. However, filtering joins filter observations from one table based on whether or not they match an observation in another table.
## Semi join
Let's start with a semi join. A semi join filters the left table down to those observations that have a match in the right table. It is similar to an inner join where only the intersection between the tables is returned, but unlike an inner join, only the columns from the left table are shown. Finally, no duplicate rows from the left table are returned, even if there is a one-to-many relationship. Let's look at an example.

For this chapter, the dataset we will use is from an online music streaming service. In this new dataset, we have a table of song genres shown here. There's also a table of top-rated song tracks. The 'gid' column connects the two tables. Let's say we want to find what genres appear in our table of top songs. A semi join would return only the columns from the genre table and not the tracks.

First, let's merge the two tables with an inner join. We also print the first few rows of the genres_tracks variable. Since this is an inner join, the returned 'gid' column holds only values where both tables matched.
```Python
genres_tracks = genres.merge(top_tracksm on='gid')
```
For the next step in the technique, let's focus on this line of code. It uses a method called isin(), which compares every 'gid' in the genres table to the 'gid' in the genres_tracks table. This will tell us if our genre appears in our merged genres_tracks table. This line of code returns a Boolean Series of true or false values.
```Python
genres['gid'].isin(genres_tracks['gid'])
>>0    True
>>1    True
>>2    True
>>3    True
>>4   False
>>Name: gid, dtype: bool
```
To combine everything, we use that line of code to subset the genres table. The results are saved to top_genres and we print a few rows. We've completed a semi join. These are rows in the genre table that are also found in the top_tracks table. This is called a filtering join because we've filtered the genres table by what's in the top_tracks table.
```Python
genres_tracks = genres.merge(top_tracks, on='gid')
top_genres = genres[genres['gid'].isin(genres_tracks['gid'])]
print(top_genres.head())
>>   gid    name
>>0  1      Rock
>>1  2      Jazz
>>2  3      Metal
>>3  4      Alternative & Punk
>>4  6      Blues
```
## Anti join
Now let's talk about anti joins. An anti join returns the observations in the left table that do not have a matching observation in the right table. It also only returns the columns from the left table. Now, let's go back to our example. Instead of finding which genres are in the table of top tracks, let's now find which genres are not with an anti join.

The first step is to use a left join returning all of the rows from the left table. Here we'll use the indicator argument and set it to True. With indicator set to True, the merge method adds a column called "\_merge" to the output. This column tells the source of each row. For example, the first four rows found a match in both tables, whereas the last can only be found in the left table.
```Python
genres_tracks = genres.merge(top_tracks, on='gid', how='left',                                      indicator=True)
```
Next, we use the "loc" accessor and "\_merge" column to select the rows that only appeared in the left table and return only the "gid" column from the genres_tracks table. We now have a list of gids not in the tracks table.
```Python
gid_list = genres_tracks.loc[genres_tracks['_merge'] == 'left_only',                                'gid']
print(gid_list.head())
>>23    5
>>34    9
>>36    11
>>37    12
>>38    13
>>Name: gid, dtype: int64
```
In our final step we use the isin() method to filter for the rows with gids in our gid_list. Our output shows those genres not in the tracks table.
```Python
genres_tracks = genres.merge(top_tracks, on='gid', how='left',                                      indicator=True)
gid_list = genres_tracks.loc[genres_tracks['_merge'] == 'left_only',                                'gid']
non_top_genres = genres[genres['gid'].isin(gid_list)]
print(non_top_genres.head())
>>   gid    name
>>0  5      Rock And Roll
>>1  9      Pop
>>2  11     Bossa Nova
>>3  12     Easy Listening
>>4  13     Heavy Metal
```
## Let's practice!
Now, your turn.
