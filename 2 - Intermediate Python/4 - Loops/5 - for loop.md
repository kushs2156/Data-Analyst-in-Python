Next to the while loop, Python features another type of loop as well: You've seen the while loop and now it's time for another loop: the for loop! Have a look at the for loop's recipe here:
```Python
for var in seq:
	expression
```
This can be read as: for each var, a variable, in seq, a sequence, execute the expressions. Makes sense?

Let's see how this actually works with an example. Remember about the fam list, containing the heights of your family? Suppose that instead of a single printout of the entire list, we want to print out each element in the list separately. You could do this by doing 4 print calls with the correct subsetting operations. Instead of this repetitive and tedious approach, you can use a for loop.
```Python
fam = [1.73, 1.68, 1.71, 1.89]

for height in fam:
	print(height)
>>1.73
>>1.68
>>1.71
>>1.89
```
Let's wipe the print calls, and start a for loop: for height in fam, followed by a colon. This means that I want to execute some code for each height in the fam list. Height is an arbitrary name here, I could just as well call it h or something else. Inside the for loop, on every iteration, I print out the value of height. When you run this script, Python encounters the for loop and evaluates the seq element, fam in this case. It sees that it's a list containing 4 elements. Then the actual iteration starts.

In the first run, Python stores the first element, so the float 1.73, in the variable height. Next, the expression, print(height), is executed, printing out 1.73. In the second iteration, Python stores the second value of fam in height, being 1.68 now, and prints out height again. This process continues until all heights in fam have been iterated over, and we end up with 4 separate printouts, great! In this solution, you don't have access to the index of the elements you're iterating over.

Say that, together with printing out the height, you also want to display the index in the list, so that the printouts are converted to this. How should the for loop be built in this case?
## enumerate
To achieve this, you can use **enumerate()**. Let's update the for loop definition like this. 
```Python
fam = [1.73, 1.68, 1.71, 1.89]

for index, height in enumerate(fam):
	print("index " + str(index) + ": " + str(height))
>>index 0: 1.73
>>index 1: 1.68
>>index 2: 1.71
>>index 3: 1.89
```
Now, enumerate(fam) produces two values on each iteration: the index of the value, and the value itself. Instead of a single variable height, you now write index, height. Now, on each iteration, index will contain the index, and height will contain the float. This means that we can now also update the statement inside the for loop with a more complicated print() call. Notice that I had to convert the floats to strings with str() so that you can add everything together. The printouts are exactly what we wanted, nice.
## Loop over string
The for loop doesn't only work with lists. You can also create a for loop that iterates over every character a string, "family" for example, and stores it in c, one after the other. 
```Python
for c in "family":
	print(c.capitalize())
>>F
>>A
>>M
>>I
>>L
>>Y
```
Inside the loop, the string c is capitalised and printed out. This time, 7 different printouts occur. That's enough on the for loop for now.
## Let's practice!
In the next videos, I'll explain how you can use the for loop to iterate over other data structures that you learned about by now, such as dictionaries and Pandas DataFrames. But for now, let's get you coding and building some for loops of your very own.