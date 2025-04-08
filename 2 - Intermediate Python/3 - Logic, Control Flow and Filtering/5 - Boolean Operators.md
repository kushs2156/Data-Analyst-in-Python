You're doing great! And now that you can produce Booleans by performing comparison operations, the next step is combining these Booleans. You can use Boolean operators for this. The three most common ones are `and`, `or`, and `not`. 
## and
The `and` operator works just as you would expect. It takes two Booleans and returns True only if both the Booleans themselves are True. This means that True and True evaluates True, but False and True, True and False and False and False all evaluate to False. Instead of using Booleans, we can of course use the results of comparisons. Suppose we have a variable x, equal to 12. To check if this variable is greater than 5 but less than 15, we can use `x > 5 and x < 15`. As you already learned, the first part will evaluate to True. The second part, will also evaluate to True. So the result of this expression, True and True, is True. This makes sense, because 12 lies between 5 and 15.
## or
The `or` operator works similarly, but the difference is that only at least one of the Booleans it uses should be True. This means that, True or True equals True, but that also False or True and True or False evaluate to True. Only False or False results in False. Also here you can make combinations with variables, like this example that checks if a variable y, which is equal to 5, is less than 7 or above 13. 5 less than 7 is True, 5 greater than 13 is False. The or operation thus returns True.
## not
Finally, there's the not operator. It simply negates the Boolean value you use it on. not True is False, not False is True. The not operation is typically useful if you're combining different Boolean operations and then want to negate that result; you'll see some examples in the exercises.
## NumPy
Now, for NumPy arrays, things are different. Retaking the bmi example from the intro course, we can try to find out which bmis are higher than 21, but lower than 22. The output of bmi greater than 21 is easily found, so is the one for the bmi lower than 22. Let's now try to combine those with the and operator I just introduced. Oops, an error. The truth value of an array with more than one element is ambiguous. and clearly doesn't like an array of Booleans to work on. 

After some digging in the NumPy documentation, you can find the functions `logical_and`, `logical_or` and `logical_not`, the "array equivalents" of and, or and not. To find out which bmis are between 21 and 22, we thus need this call. 
```Python
np.logical_and(bmi > 21, bmi < 22)
>>array([True, False, True, False, True], dtype=bool)
```
Again, as we expect from NumPy, the and operation is performed element-wise: True and True give True, like these ones, but False and True or True and False give False, like for these elements. To actually select only these bmis from the bmi array, we can use the resulting array of Booleans in square brackets. 
```Python
bmi[np.logical_and(bmi > 21, bmi < 22)]
>>array([21.852, 21.75, 21.441])
```
Again, NumPy wins when it comes to writing short yet very expressive Python code. I can hear you asking, "Cool, but how does this work for Pandas DataFrames, the de facto standard for dataset manipulation?" That's something you'll find out later in this chapter.
## Let's practice!
First try to ace the exercises that follow, and I'll see you in the next video!