In this video, I'm going to introduce you to functions. Once you learn about them you won't be able to stop using them. I sure can't. Functions aren't entirely new for you actually: you've already used them. type(), for example, is a function that returns the type of a value. But what is a function? Simply put, a function is a piece of reusable code, aimed at solving a particular task. You can call functions instead of having to write code yourself. Maybe an example can clarify things here.
## Example
Suppose you have the list containing only the heights of your family, fam: Say that you want to get the maximum value in this list. Instead of writing your own piece of Python code that goes through the list and finds the highest value, you can also use Python's max function. This is one of Python's built-in functions, just like type. We simply pass fam to max inside parentheses. 
```Python
fam = [1.73, 1.68, 1.71, 1.89]

max(fam)
>>1.89
```
The output makes sense: 1.89, the highest number in the list. max worked kind of like a black box here. You passed it a list, then the implementation of max, that you don't know, did its magic, and produced an output. How max actually did this, is not important to you, it just does what it's supposed to, and you didn't have to write your own code, which made your life easier. Of course, it's possible to also assign the result of a function call to a new variable, like here. 
```Python
tallest = max(fam)
tallest
>>1.89
```
Now tallest is just like any other variable; you can use it to continue your fancy calculations.
## round()
Another one of these built-in functions is round. It takes two inputs: first, a number you want to round, and second, the precision with which to round, which is how many digits after the decimal point you want to keep. Say you want to round 1.68 to one decimal place. The first input is 1.68, the second input is 1. You separate the inputs with a comma. 
```Python
round(1.68, 1)
>>1.7
```
But there's more. It's perfectly possible to call the round function with only one input, like this. This time, Python figured out that you didn't specify the second input, and automatically chooses to round the number to the closest integer. 
```Python
round(1.68)
>>2
```
To understand why both approaches work, let's open up the documentation. You can do this with yet another function, help, like this. 
```Python
help(round) #Open up documentation
>>Help on built-in function round in module builtins:
>>
>>round(number, ndigits=None)
>>	Round a number to a given precision in decimal digits.
>>
>>	The return value is an integer if ndigits is omitted or None.
>>	Otherwise the return value has the same type as the number. 
>>	ndigits may be negative.
```
It appears that round takes two inputs. In Python, these inputs, also called arguments, have names: number and ndigits. When you call the function round, with these two inputs, Python matches the inputs to the arguments: number is set to 1.68 and ndigits is set to 1. Next, the round function does its calculations with number and ndigits as if they are Python variables in a script. We don't know exactly what code Python executes. What is important, though, is that the function produces an output, namely the number 1.68 rounded to 1 decimal place. If you call the function round with only one input, Python again tries to match the inputs to the arguments. There's no input to match to the ndigits argument though. Luckily, the internal machinery of the round function knows how to handle this. When ndigits is not specified, the function simply rounds to the closest integer and returns that integer. That's why we got the number 2. In other words, ndigits is an optional argument. This tells us that you can call round in this form, as well as in this one.
```Python
round(number)
round(number, ndigits)
```
## Find functions
By now, you have an idea about how to use max and round, but how could you know that a function such as round exists in Python in the first place? Well, this is something you will learn with time. Whenever you are doing a rather standard task in Python, you can be pretty sure that there's already a function that can do this for you. In that case, you should definitely use it! Just do a quick internet search and you'll find the function you need with a nice usage example. And there is of course DataCamp, where you'll also learn about powerful functions and how to use them.
## Let's practice!
Get straight to it in the interactive exercises, and I'll see you back here soon!