Hello again! In this lesson, we will talk about merging a table to itself. This type of merge is also referred to as a self join. So, let's get started. 

So when would you ever need to merge a table to itself? The table shown here is called sequels and has three columns. It contains a column for movie id, title, and sequel. The sequel number refers to the movie id that is a sequel to the original movie. For example, in the second row the movie is titled Toy Story, and has an id equal to 862. The sequel number of this row is 863. This is the movie id for Toy Story 2, the sequel to Toy Story. If we continue, 10193 is the movie id Toy Story 3 which is the sequel for Toy Story 2.

If we would like to see a table with the movies and the corresponding sequel movie in one row of the table, we will need to merge the table to itself. In the left table, the sequel ID for Toy Story of 863 is matched with 863 in the ID column of the right table. Similarly, Toy Story 2 of the left table is matched with Toy Story 3 in the right table. We will talk more about this later, but the merge is an inner join. Therefore, we do not see Avatar and Titanic because they do not have sequels.

To complete this merge, we set the sequels table as input to the merge method for both the left and right tables. We can think of it as merging two copies of the same table. All of the aspects we have reviewed regarding merging two tables still apply here. Therefore, we can merge the tables on different columns. We'll use the 'left_on' and 'right_on' attributes to match rows where the sequel's id matches the original movie's id. Finally, setting the suffixes argument in the merge method allows us to identify which columns describe the original movie and which describe the sequel. 
```Python
original_sequels = sequels.merge(sequels, left_on='sequel',
								 right_on='id',
								 suffixes=('_org', '_seq'))

print(original_sequels[['title_org', 'title_seq']].head())
```
When we look at the results of the merge, the 'title_org' and 'title_seq' list the original and sequel movies, respectively. Here we listed the original movie and its sequel in one row. Now that we have our result table from the merge, we could select only the `title_org`, and `title_seq` columns, and we can see that we've successfully linked each movie to its sequel.
## Merging a table to itself with left join
Pausing here is a good time to highlight again that when merging a table to itself, we can use the different types of joins we have already reviewed. Let's take the same merge from earlier but make it a left join. The 'how' argument is set in the merge method to left from the default 'inner'. 
```Python
original_sequels = sequels.merge(sequel, left_on='sequel',
								 right_on='id', how='left',
								 suffixes=('_org', '_seq'))
```
Now the resulting table will show all of our original movie info. If the sequel movie exists in the table, it will fill out the rest of the row. If you compare this to our earlier merger, you now see movies like Avatar and Titanic in the result set.
## When to merge a table to itself
You might need to merge a table to itself when working with tables that have a hierarchical relationship, like employee and manager. You might use this on sequential relationships such as logistic movements. Graph data, such as networks of friends, might also require this technique.
## Let's practice!
Alright, let's practice merging a table to itself.