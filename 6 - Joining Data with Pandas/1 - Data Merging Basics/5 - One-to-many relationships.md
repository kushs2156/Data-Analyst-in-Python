Welcome back! In the last lesson, we learned how to merge two DataFrames together with the merge method. In this lesson, we'll discuss different types of relationships between tables. In particular, we will discuss the one-to-many relationship. But first, let's quickly consider what a one-to-one relationship is.
## One-to-one relationship
In a one-to-one relationship, every row in the left table is related to one and only one row in the right table. We looked at a one-to-one relationship earlier. Recall the relationship between the wards table and the census table. Every row in the wards table is related to only one row in the census table, so there is only one row for ward 3 in each table. Practically speaking, it only makes sense that there is one row of population information for each ward. It wouldn't make sense if the census table contained multiple population values in 2000 for the third ward.
## One-to-many relationship
So, what is a one-to-many relationship? Well, in a one-to-many relationship, every row in the left table is related to one or more rows in the right table. To provide an example of a one-to-many relationship, let's think back to our wards table. Within each ward, there are many businesses. We will merge the wards table with a table of licensed businesses in each ward. The business license data is stored in another table called licenses. It holds info such as the business address and ward the business is located within. The two DataFrames are related to each other by their ward column.

When we merge the two tables together with the merge method, setting the 'on' attribute to the column ward, the resulting table has both local ward data and business license data. Notice that ward 1 and its alderman Joe is repeated in the resulting table because the licenses table has many businesses in the 1st ward. pandas takes care of the one-to-many relationships for us and doesn't require anything special on our end. We can use the same syntax as we did with one-to-one relationships.
```Python
ward_licenses = ward.merge(licenses, on='ward', suffexes=('_ward', '_lic'))
```
By printing the shape, we can see that our original wards table has 50 rows. After merging the wards table with the licenses table, the resulting table has 10,000 rows. When you merge tables that have a one-to-many relationship, the number of rows returned will likely be different than the number in the left table.
```Python
print(wards.shape)
>>(50, 4)

print(wards_licenses.shape)
>>(10000, 4)
```
## Let's practice!
Now let's make the one-to-many relationship idea more concrete by practicing.