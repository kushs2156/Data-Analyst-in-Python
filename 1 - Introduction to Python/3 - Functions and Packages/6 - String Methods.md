- Use the `.upper()` [method](https://docs.python.org/3/library/stdtypes.html#str.upper) on `place` and store the result in `place_up`. Use the syntax for calling methods that you learned in the previous video.
- Print out `place` and `place_up`. Did both change?
- Print out the number of o's on the variable `place` by calling `.count()` on `place` and passing the letter `'o'` as an input to the method. We're talking about the variable `place`, not the word `"place"`!
```Python
# string to experiment with: place
place = "poolhouse"

# Use upper() on place
place_up = place.upper()

# Print out place and place_up
print(place)
print(place_up)
>>poolhouse
>>POOLHOUSE

# Print out the number of o's in place
print(place.count('o'))
3
```
