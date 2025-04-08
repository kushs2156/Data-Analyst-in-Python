Write a `for` loop that goes through each sublist of `house` and prints out `the x is y sqm`, where x is the name of the room and y is the area of the room.
```Python
# house list of lists
house = [["hallway", 11.25], 
         ["kitchen", 18.0], 
         ["living room", 20.0], 
         ["bedroom", 10.75], 
         ["bathroom", 9.50]]
# Build a for loop from scratch
for i in house:
    print("the " + str(i[0]) + " is " + str(i[1]) + " sqm")
>>the hallway is 11.25 sqm 
>>the kitchen is 18.0 sqm 
>>the living room is 20.0 sqm 
>>the bedroom is 10.75 sqm 
>>the bathroom is 9.5 sqm
```
