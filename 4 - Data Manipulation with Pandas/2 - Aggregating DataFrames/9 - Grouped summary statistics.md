So far, you've been calculating summary statistics for all rows of a dataset, but summary statistics can be useful to compare different groups. 

While computing summary statistics of entire columns may be useful, you can gain many insights from summaries of individual groups. For example, does one colour of dog weigh more than another on average? Are female dogs taller than males? You can already answer these questions with what you've learned so far! We can subset the dogs into groups based on their colour, and take the mean of each. 
```Python
dogs[dogs["color"] == "Black"]["weight_kg"].mean()
dogs[dogs["color"] == "Brown"]["weight_kg"].mean()
dogs[dogs["color"] == "White"]["weight_kg"].mean()
dogs[dogs["color"] == "Gray"]["weight_kg"].mean()
dogs[dogs["color"] == "Tan"]["weight_kg"].mean()
```
But that's a lot of work, and the duplicated code means you can easily introduce copy and paste bugs.
## Grouped summaries
That's where the `.groupby()` method comes in. We can group by the color variable, select the weight column, and take the mean. This will give us the mean weight for each dog colour. This was just one line of code compared to the five we had to write before to get the same results.
```Python
dogs.groupby("color")["weight_kg"].mean()
>>color
>>Black    26.5
>>Brown    24.0
>>Gray     17.0
>>Tan      2.0
>>White    74.0
>>Name: weight_kg, dtype: float64
```
## Multiple grouped summaries
Just like with ungrouped summary statistics, we can use the agg method to get multiple statistics. Here, we pass a list of functions into agg after grouping by color. This gives us the minimum, maximum, and sum of the different coloured dogs' weights.
```Python
dogs.groupby("color")["weight_kg"].agg([min, max, sum])
>>       min   max   sum
>>color       
>>Black   24    29    53
>>Brown   24    24    48
>>Gray    17    17    17 
>>Tan      2     2     2 
>>White   74    74    74 
```
## Grouping by multiple variables
You can also group by multiple columns and calculate summary statistics. Here, we group by colour and breed, select the weight column and take the mean. This gives us the mean weight of each breed of each colour.
```Python
dogs.groupby(["color", "breed"])["weight_kg"].mean()
```
You can also group by multiple columns and aggregate by multiple columns.
```Python
dogs.groupby(["color", "breed"])[["weight_kg", "height_cm"]].mean()
```
## Let's practice!
Now that we've talked about grouping, it's time to practice grouped summary statistics.