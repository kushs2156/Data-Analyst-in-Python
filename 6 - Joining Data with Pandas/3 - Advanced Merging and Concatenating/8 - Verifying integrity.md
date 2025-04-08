Welcome back. In this lesson, let's talk about verifying the integrity of our data. Both the `merge` and `concat` methods have special features that allow us to verify the structure of our data. When merging two tables, we might expect the tables to have a one-to-one relationship. However, one of the columns we are merging on may have a duplicated value, which will turn the relationship into a one-to-many. When concatenating tables vertically, we might unintentionally create duplicate records if a record exists in both tables. The `validate` and `verify_integrity` arguments of the merge and concat methods respectively will allow us to verify the data.
## Validating merges
Let's start with the merge method. If we provide the validate argument one of these key strings, it will validate the relationship between the two tables.

| .merge(validate=None) |
| --------------------- |
| 'one_to_one'          |
| 'one_to_many'         |
| 'many_to_one'         |
| 'many_to_many'        |
For example, if we specify we want a one-to-one relationship, but it turns out the relationship is not one-to-one, then an error is raised. Let's try it out.
## Merge dataset for example
In this example, we want to merge these two tables on the column "tid". Again, our data is from our music service. The first table is named "tracks", and the second is called "specs" for the technical specifications of each track. Each track should have one set of specifications, so this should be a one-to-one merge. However, notice that the specs table has two rows with a "tid" value equal to two. Therefore, merging these tables now becomes, unintentionally, a one-to-many relationship.
## Merge validate: one_to_one
Let's merge the two tables with the tracks table on the left and specs on the right. Additionally, let's set the validate argument equal to one_to_one. In the result, a MergeError is raised. 
```Python
tracks.merge(specs, on='tid',
			 validate='one_to_one')
>>Traceback (most recent call last):
>>MergeError: Merge keys are not unique in right dataset; not a one-to-one merge
```
Python then tells us that the right table has duplicates, so it is not a one-to-one merge. We know that we should handle those duplicates properly before merging.
## Merge validate: one_to_many
Now we'll merge album information with the tracks table. For every album there are multiple tracks, so this should be a one-to-many relationship. When we set the validate argument to "one_to_many" no error is raised.
```Python
albums.merge(tracks, on='aid',
			 validate='one_to_many')
```
## Verifying concatenations
Let's now talk about the concat method. It has the argument `verify_integrity`, which by default is False. However, if set to True, it will check if there are duplicate values in the index and raise an error if there are. It will only check the index values and not the columns.

To try out this feature, we will attempt to concatenate these two tables. They are the February and March invoice data shown in a previous video. However, both tables were modified so the index contains invoice IDs. Notice that invoice ID number 9 is in both tables.

Let's try to concatenate the two tables together with the verify_integrity argument set to True. 
```Python
pd.concat([inv_feb, inv_mar],
		   verify_integrity=True)

pd.concat([inv_feb, inv_mar],
		   verify_integrity=False)
```
The concat method raises a ValueError stating that the indexes have overlapping values. Now let's try to concatenate the two tables again with the verify_integrity set back to the default value of False. The concat method now returns a combined table with the invoice ID of number 9 repeated twice.
## Why verify integrity and what to do
Often our data is not clean, and it may not always be evident if data has the expected structure. Therefore, verifying this structure is useful, saving us from having a mean skewed by duplicate values, or from creating inaccurate plots. If you receive a MergeError or a ValueError, you can fix the incorrect data or drop duplicate rows. In general, you should look to correct the issue.
## Let's practice!
Time for some practice!