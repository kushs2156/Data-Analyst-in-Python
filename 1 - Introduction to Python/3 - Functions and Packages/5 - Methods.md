Built-in functions are only one part of the Python story. You already know about functions such as max, to get the maximum of a list, len, to get the length of a list or a string, and so on. But what about other basic things, such getting the index of a specific element in the list, or reversing a list? You can look very hard for built-in functions that do this, but you won't find them.
## Back 2 Basics
In the past exercises, you've already created a bunch of variables. Among other Python types, you've created strings, floats and lists. Each one of these values or data structures are so-called Python objects. This string is an object, this float is an object, but this list is also, you got it, an object. These objects have a specific type, that you already know: string, float, and list, and of course they represent the values you gave them, such as "liz", 1.73 and an entire list. But in addition to this, Python objects also come with a bunch of so-called "methods". You can think of methods as functions that "belong to" Python objects. A Python object of type string has methods, such as capitalize() and replace(), but also objects of type float and list have specific methods depending on the type. Enough for the theory now; let's try to use a method!
## list methods
Suppose you want to get the index of the string "mom" in the fam list. fam is an Python object with the type list, and has a method named index. 
```Python
fam
>>['liz', 1.73, 'emma', 1.68, 'mom', 1.71, 'dad', 1.89]
```
To call the method, you use the dot notation, like this. The only input is the string "mom", the element you want to get the index for. 
```Python
fam.index("mom") # Call method index() on fam
>>4
```
Python returns 4, which indeed is the index of the string "mom". I called the index method "on" the fam list here, and the output was 4. Similarly, I can use the count method on the fam list to count the number of times 1.73 occurs in the list. 
```Python
fam.count(1.73)
>>1
```
Python gives me 1, which makes sense, because only liz is 1.73 meters tall. But lists are not the only Python objects that have methods associated. Also floats, integers, Booleans and strings are Python objects that have specific methods associated with them.
## str methods
Take the variable sister for example, that represents a string. 
```Python
sister
>>'liz'
```
You can call the method capitalize on sister, without any inputs. It returns a string where the first letter is capitalized now. 
```Python
sister.capitalize()
>>'Liz'
```
Or what if you want to replace some parts of the string with other parts? Not a problem. Just call the method replace on sister, with two appropriate inputs. 
```Python
sister.replace("z", "sa")
>>'lisa'
```
In the output, "z" is replaced with "sa".
## Methods
To be absolutely clear: in Python, everything is an object, and each object has specific methods associated. Depending on the type of the object, list, string, float, whatever, the available methods are different. A string object like sister has a replace method, but a list like fam doesn't have this. Objects of different types can have methods with the same name: Take the index method. It's available for both strings and lists. If you call it on a string, you get the index of the letters in the string; If you call it on a list, you get the index of the element in the list. This means that, depending on the type of the object, the methods behave differently. 

Before I unleash you on some exercises on methods, there's one more thing I want to tell you. Some methods can change the objects they are called on. Let's retake the fam list, and call the append method on it. As the input, we pass a string we want to add to the list. 
```Python
fam
>>['liz', 1.73, 'emma', 1.68, 'mom', 1.71, 'dad', 1.89]

fam.append("me")

fam
>>['liz', 1.73, 'emma', 1.68, 'mom', 1.71, 'dad', 1.89, 'me']

fam.append(1.79)
fam
>>['liz', 1.73, 'emma', 1.68, 'mom', 1.71, 'dad', 1.89, 'me'. 1.79]
```
Python doesn't generate an output, but if we check the fam list again, we see that it has been extended with the string "me". Let's do this again, this time to add my height to the list. Again, the fam list was extended. This is pretty cool, because you can write very concise code to update your data structures on the fly, but it can also be pretty dangerous. Some method calls don't change the object they're called on, while others do, so watch out.
## Summary
Let's take a step back here and summarise this. You have Python functions, like type, max and round, that you can call. There's also methods, which are functions that are specific to Python objects. Depending on the type of the Python object you're dealing with, you'll be able to use different methods and they behave differently. You can call methods on the objects with the dot notation. There's much more to tell about Python objects, methods and how Python works internally, but for now, let's stick to what I've talked about here.
## Let's practice!
It's time to get some exercises and add methods to your evergrowing skillset!