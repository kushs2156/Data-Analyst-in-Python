To see if you completely understood the boolean operators, have a look at the following piece of Python code:

```Python
x = 8
y = 9
not(not(x < 3) and not(y > 14 or y > 10))
```

What will the result be if you execute these three commands?

_NB: Notice that `not` has a higher priority than `and` and `or`, it is executed first._
- False