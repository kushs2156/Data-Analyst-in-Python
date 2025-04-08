- **Inside** the `while` loop, complete the `if`-`else` statement:
    - If `offset` is greater than zero, you should decrease `offset` by 1.
    - Else, you should increase `offset` by 1.
- If you've coded things correctly, hitting _Submit Answer_ should work this time.

_If your code is still taking too long to run (or your session is expiring), you probably made a mistake. Check your code and make sure that the statement `offset != 0` will eventually evaluate to `FALSE`!_
```Python
# Initialize offset
offset = -6

# Code the while loop
while offset != 0 :
    print("correcting...")
    if offset > 0 :
      offset = offest - 1
    else : 
      offset = offset + 1    
    print(offset)
```

