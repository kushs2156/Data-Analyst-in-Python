Now that you have learned quite a bit about combining data from different data sources, let's review a pandas method for selecting data from the table called the `query()` method. pandas provides many methods for selecting data, and query() is one of them.
## The `.query()` method
The query() method accepts an input string that it will use to select rows to return from the table. For those familiar with SQL, the string you provide to the query function is similar to the portion after the WHERE clause of a SQL statement. However, don't let the SQL statement scare you, because prior knowledge of SQL isn't required. Let's look at an example.

We have the following table named stocks with the stock price of Disney and Nike on different days. Now imagine we would like to select the rows where Nike is equal to or above 90. Here we provide a string to the query method. The string identifies that we want to condition which rows are returned by the value of the Nike column. We simply input `'nike >= 90'`. The method returns all rows in stocks where Nike is greater than or equal to 90.
## Querying on multiple conditions
Let's look at another example. Here we use the "and" keyword to select rows where Nike is greater than 90 and Disney is less than 140. The method returns two rows of data that match our criteria. 
```Python
stocks.query('nike > 90 and disney < 140')

stocks.query('nike > 96 or disney < 98')
```
Next, instead of using "and" we can also use the "or" keyword. This input string should select all rows where Nike is over 96 or Disney is less than 98. Now the function returns three rows that meet our criteria.
## Using `.query()` to select text
Our next example shows that you can use the query method to select strings. Imagine now that we have an updated dataset, which is the stocks table in a slightly different format. We are interested in selecting all of the rows were the column stock equals "disney" or the column stock equals "nike" and close is less than 90. Let's pause here for a moment to look at our query string. 
```Python
stocks_long.query('stock=="disney" or (stock=="nike" and close < 90)')
```
Within the parentheses of our string, we check if the stock column is nike and the close column is less than 90. Both of these conditions have to be true for the parentheses section to return true. We then add that to the condition to check if stock is listed as "disney". When checking text, we use the double equal signs, similar to an if statement in Python. Also, when checking a text string, we used double quotes to surround the word. This is to avoid unintentionally ending our string statement since we used single quotes to start the statement. In our results, we see all of our Disney rows returned. Also, those rows were Nike is the stock name and the close price is less than 90 are returned.
## Let's practice!
It's time for you to try using the query() method.