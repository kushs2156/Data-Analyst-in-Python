So you know about comparison operators now, such as less than and greater than, and you also know how to combine the Boolean results, using Boolean operators such as and and or. Things get really interesting when you can actually use these concepts to change how your program behaves. Depending on the outcome of your comparisons, you might want your Python code to behave differently. You can do this with conditional statements in Python: `if`, `else` and `elif`.
## if
Let's start working in a script, `control.py`. Suppose you have a variable z, equal to 4. If the value is even, you want to print out: "z is even". This code does the trick. modulo operator 2 will return 0 if z is even. 
```Python
if condition:
	expression

z = 4
if z % 2 == 0:    # True
	print("z is even")
>>z is even
```
If you run this, Python checks if the condition holds. It's true, so the corresponding code is executed: "z is even" gets printed out. Let's compare this to the general recipe for an if statement. It reads as follows: if condition, execute expression. Notice the colon at the end, and the fact that you simply have to indent the Python code with four spaces (or a tab) to tell Python what to do in the case the condition succeeds. To exit the if statement, simply continue with some Python code without indentation, and Python will know that it's not part of the if statement. 

It's perfectly possible to have more lines inside the if statement, like this for example. The script now prints out two lines if you run it. If the condition does not pass, the expression is not executed.
```Python
z = 4
if z % 2 == 0:    # True
	print("checking" + str(z))
	print("z is even")
>>checking 4
>>z is even
```
You can see this if we change z to be 5 and rerun the code: there's no output.
```Python
z = 5
if z % 2 == 0:    # False
	print("checking" + str(z))
	print("z is even")
```
Suppose now that you want to print out "z is odd" in this case. How to do this?
## else
Well, you can simply use an else statement, like this. If we run it with z equal to 5, the condition is not true, so the expression for the else statement gets printed out. 
```Python
if condition:
	expression
else:
	expression

z = 5
if z % 2 == 0:    # False
	print("z is even")
else:
	print("z is odd")
>>z is odd
```
The general recipe looks like this: for the else statement, you don't need to specify a condition. The corresponding expression gets run if the condition of the if statement it belongs to does not hold.
## elif
You can think of cases where even more customised behaviour is necessary. Say you want different printouts for numbers that are divisible by 2 and by 3. You can throw some elifs in there to get the job done. Take this example. Can you tell what this script will print out if you run it? 
```Python
if condition:
	expression
elif condition:
	expression
else:
	expression

z = 3
if z % 2 == 0:
	print("z is divisible by 2") # False
elif z % 3 == 0:
	print("z is divisible by 3") # True
else:
	print("z is neither divisible by 2 nor by 3")
>>z is divisible by 3
```
If z equals 3, the first condition is False, so it goes over to the next condition. This condition, does hold, so the corresponding print statement is executed.

Suppose now that z equals 6. Both the if and elif conditions hold in this case. Will two printouts occur? Nope. As soon as Python bumps into a condition that is true, it executes the corresponding code and then leaves the control structure after that. This means the second condition, corresponding to the elif, is never reached so there's no corresponding printout.
```Python
z = 6
if z % 2 == 0:
	print("z is divisible by 2") # True
elif z % 3 == 0:
	print("z is divisible by 3") # Never reached
else:
	print("z is neither divisible by 2 nor by 3")
>>z is divisible by 2
```
## Let's practice!
Control flow can be extremely powerful when you're writing your own Python scripts. Get some practice with it in the exercises!