After you've created your very own Python list, you'll need to know how you can access information in the list.
## Subsetting lists
Python uses the index to do this. Have a look at the fam list again here. 
```Python
fam = ['liz', 1.73, 'emma', 1.68, 'mom', 1.71, 'dad', 1.89]
```
The first element in the list has index 0, the second element has index 1, and so on. Suppose that you want to select the height of Emma, the float 1.68. It's the fourth element, so it has index 3. To select it, you use 3 inside square brackets. Similarly, to select the string "dad" from the list, which is the seventh element in the list, you'll need to put the index 6 inside square brackets.
```Python
fam[3]
>>1.68
fam[6]
>>'dad'
```
You can also count backwards, using negative indexes. This is useful if you want to get some elements at the end of your list. To get your dad's height, for example, you'll need the index -1. These are the negative indexes for all list elements.
```Python
fam[-1]
>>1.89
fam[7]
>>1.89
```
This means that both these lines return the exact same result. 
## List slicing
Apart from indexing, there's also something called slicing, which allows you to select multiple elements from a list, thus creating a new list. You can do this by specifying a range, using a colon. Let's first have another look at the list, and then try this piece of code. Can you guess what it'll return? A list with the the float 1.68, the string "mom", and the float 1.71, corresponding to the 4th, 5th and 6th element in the list maybe? Let's see what the output is. 
```Python
fam[3:5]
>>[1.68, 'mom']
```
Apparently, only the elements with index 3 and 4, get returned. The element with index 5 is not included. In general, this is the syntax: the index you specify before the colon, so where the slice starts, is included, while the index you specify after the colon, where the slice ends, is not. With this in mind, can you tell what this call will return? 
```Python
fam[1:4]
>>[1.73, 'emma', 1.68]
```
You probably guessed correctly that this call gives you a list with three elements, corresponding to the elements with index 1, 2 and 3 of the fam list. You can also choose to just leave out the index before or after the colon.

If you leave out the index where the slice should begin, you're telling Python to start the slice from index 0, like this example. If you leave out the index where the slice should end, you include all elements up to and including the last element in the list, like here. 
```Python
fam[:4]
>>['liz', 1.73, 'emma', 1.68]

fam[5:]
>>[1.71, 'dad', 1.89]
```
## Let's practice!
Now it's time to head over to the exercises, where you will continue to work on the list you've created yourself before. You'll use different subsetting methods to get exactly the piece of information you need!