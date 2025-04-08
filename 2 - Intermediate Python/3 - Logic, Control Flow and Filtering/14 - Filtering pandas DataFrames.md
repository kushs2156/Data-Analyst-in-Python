In previous videos, I gave some examples of how the NumPy array can be useful to do comparison operations and Boolean operations on an element-wise basis. Let's now use this knowledge on the Pandas DataFrame.

For starters, let's import the BRICS dataset again from the CSV file; here it is.
```Python
import pandas as pd
brics = pd.read_csv("path/to/brics.csv", index_col = 0)
brics
```

|     | country      | capital   | area   | population |
| --- | ------------ | --------- | ------ | ---------- |
| BR  | Brazil       | Brasilia  | 8.516  | 200.40     |
| RU  | Russia       | Moscow    | 17.100 | 143.50     |
| IN  | India        | New Delhi | 3.286  | 1252.00    |
| CH  | China        | Beijing   | 9.597  | 1357.00    |
| SA  | South Africa | Pretoria  | 1.221  | 25.98      |
Suppose you now want to keep the countries, so the observations in this case, for which the area is greater than 8 million square kilometres. There are three steps to this. First of all, we want to get the area column from brics. Next, we perform the comparison on this column and store its result. Finally, we should use this result to do the appropriate selection on the DataFrame.
## Step 1: Get column
So the first step, getting the area column from brics. There are many different ways to do this. What's important here, is that we ideally get a Pandas Series, not a Pandas DataFrame. Let's do this with square brackets, like this. This loc alternative, and this iloc version, would also work perfectly fine.
```Python
brics["area"] # All result in a Pandas Series
brics.loc[:,"area"]
brics.iloc[:, 2]
```
## Step 2: Compare
Next, we actually perform the comparison. To see which rows have an area greater than 8, we simply append greater than 8 to the code from before, like this. Now we get a Series containing booleans. If you compare it to the actual area values, you can see that the areas with a value over 8 correspond to True, and the ones with a value under 8 correspond to False now. Let me store this Boolean Series as `is_huge`.
```Python
is_huge = brics["area"] > 8

is_huge
>>BR    True
>>RU    True
>>IN    False
>>CH    True
>>SA    False
>>Name: area, dtype: bool
```
## Step 3: Subset DF
The final step is using this Boolean Series to subset the Pandas DataFrame. This is something I haven't shown you yet. To do this, you put `is_huge` inside square brackets. The result is exactly what we want: only the countries with an area greater than 8, namely Brazil, Russia and China.
```Python
brics[is_huge]
```

|     | country | capital  | area   | population |
| --- | ------- | -------- | ------ | ---------- |
| BR  | Brazil  | Brasilia | 8.516  | 200.40     |
| RU  | Russia  | Moscow   | 17.100 | 143.50     |
| CH  | China   | Beijing  | 9.597  | 1357.00    |
## Summary
So let's summarise this: I selected the area column, performed a comparison on this column and the stored it as is_huge so that I can use it to index the brics DataFrame. These different commands do the trick. However, we can also write this in a one-liner: simply put the code that defines is_huge directly in the square brackets. Great!
```Python
brics[brics["area"] > 8]
```
## Boolean operators
Now we haven't used Boolean operators yet. Remember that we used this `logical_and` function from the NumPy package to do an element wise Boolean operation on NumPy arrays? Because Pandas is built on NumPy, you can also use that function here. Suppose you only want to keep the observations that have an area between 8 and 10 million square kilometres. After importing numpy as np, we can use the logical_and() function to create a Boolean Series. The only thing left to do is placing this code inside square brackets to subset brics appropriately. 
```Python
import numpy as np

brics[np.logical_and(brics["area"] > 8, brics["area"] < 10)]
```
This time, only Brazil and China are included. Russia has an area of 17 million square kilometres, which doesn't meet the conditions. I hope these examples have shown you how easy it is to filter DataFrames to get interesting results.
## Let's practice!
Get some hands-on experience in the exercises yourself! And I'll see you in the next chapter where we'll get even more of our control flow on.