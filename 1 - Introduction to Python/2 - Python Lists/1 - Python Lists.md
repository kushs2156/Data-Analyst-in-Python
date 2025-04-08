Welcome back aspiring Pythonista. By now, you've played around with different data types, and I hope you've had as much fun as I have.
## Python Data Types
On the numbers side, there's the float, to represent a real number, and the int, to represent an integer. Next, we also have str, short for string, to represent text in Python, and bool, which can be either True or False. You can save these values as a variable, like these examples show. Each variable then represents a single value. 
## Problem
As a data scientist, you'll often want to work with many data points. If you for example want to measure the height of everybody in your family, and store this information in Python, it would be inconvenient to create a new python variable for each point you collected right? What you can do instead, is store all this information in a Python list.
## Python List
You can build such a list with square brackets. Suppose you asked your two sisters and parents for their height, in meters. You can build the list as follows: Of course, also this data structure can be referenced to with a variable. Simply put the variable name and the equals sign in front, like here. 
```Python
fam = [1.73, 1.68, 1.71, 1.89]
```
A list is a way to give a single name to a collection of values. These values, or elements, can have any type; they can be floats, integer, Booleans, strings, but also more advanced Python types, even lists. It's perfectly possible for a list to contain different types as well.

Suppose, for example, that you want to add the names of your sisters and parents to the list, so that you know which height belongs to who. You can throw in some strings without issues. 
```Python
fam = ['liz', 1.73, 'emma', 1.68, 'mom', 1.71, 'dad', 1.89]
```
But that's not all. I just told you that lists can also contain lists themselves. Instead of putting the strings in between the numbers, you can create little sublists for each member of the family. One for Liz, one for Emma and so on. Now, you can tell Python that these sublists are the elements of another list, that I named fam2: the little lists are wrapped in square brackets and separated with commas. 
```Python
fam2 = [["liz", 1.73],
	    ["emma", 1.68],
	    ["mom", 1.71],
	    ["dad"], 1.89]
```
If you now print out fam2, you see that we have a list of lists. The main list contains 4 sub-lists. We're dealing with a new Python type here, next to the strings, Booleans, integers and floats you already know about: the list.
```Python
type(fam)
>>list
type(fam2)
>>list
```
These calls show that both fam and fam2 are lists. Remember that I told you that each type has specific functionality and behaviour associated? Well, for lists, this is also true. Python lists host a bunch of tools to subset and adapt them. But let's take this step by step, and have you experiment with list creation first!