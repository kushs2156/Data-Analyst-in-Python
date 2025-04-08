In this lesson we will talk about another method for ordered or time-series data called merge_asof().
## Using merge_asof()
The merge_asof() method is similar to an ordered left join. It has similar features as merge_ordered(). However, unlike an ordered left join, merge_asof() will match on the nearest value columns rather than equal values. This brings up an important point - whatever columns you merge on must be sorted. In the table shown here, when we merge on column "C", we bring back all of the rows from the left table. However, the row selected from the right table is the last row whose "C" value is less than or equal to the "C" value in the left table. So, for example, the second row in the left table is matched with the third row in the right table. This because 3 is the closest value in the right table that is still less than or equal to 5.
## Datasets
For this example, we will look at merging two tables. The first is stock price data for the Visa company with entries for every hour on Nov, 11, 2017. The second table is IBM stock prices on the same day with entries for roughly every five minutes.
## `merge_asof()` example
Let's use merge_asof() to merge the tables. The input arguments are very similar to what we have already seen in the course. Here we list the left and right tables first. Then we define that we want to merge on the "date_time" column. Finally, we provide a set of suffixes. 
```Python
pd.merge_asof(visa, ibm, on='date_time',
			  suffixes=('_visa', '_ibm'))
```
Our output is similar to a left join, so we see all of the rows from the left Visa table. However, the values from the IBM table are based on how close the date_time values match with the Visa table. Notice the first row and the IBM price of 149.11. Let's show the IBM table again and see why this value was chosen in the merger. It comes from the row indexed as 4. This row has the closest date_time that is less than the date_time in the Visa table. The next row has a date_time that is slightly greater. We will adjust this behaviour in our coming example.
## `merge_asof()` example with direction
This time in our merge_asof() method, we list the direction argument as "forward". This will change the behaviour of the method to select the first row in the right table whose "on" key column is greater than or equal to the left's key column. The default value for the direction argument is "backward". 
```Python
pd.merge_asof(visa, ibm, on=['date_time'],
			  suffixes=('_visa', '_ibm'),
			  direction='forward')
```
When we look at our results, we see different values for the IBM column. Let's again look at the first IBM value and trace it back to the IBM table. We see it in the row indexed as 5. Its date_time is slightly greater than the date_time in the visa table. Finally, you can set the direction argument to "nearest" which returns the nearest row in the right table regardless if it is forward or backwards.
## When to use `merge_asof()`
Now that we reviewed the merge_asof() method, here are a couple of thoughts on when you might want to use it. First, you might think of this method when you are working with data sampled from a process and the dates or times may not exactly align. This is similar to what we did in our example. It could also be used when you are working on a time-series training set, where you do not want any events from the future to be visible before that point in time.
## Let's practice!
