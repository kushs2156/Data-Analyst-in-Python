- Perform a selective import from the `math` package where you only import the `pi` function.
- Use `math.pi` to calculate the circumference of the circle and store it in `C`.
- Use `math.pi` to calculate the area of the circle and store it in `A`.
```Python
# Import pi function of math package
from math import pi

# Calculate C
C = 2 * 0.43 * pi

# Calculate A
A = pi * 0.43 ** 2

print("Circumference: " + str(C))
print("Area: " + str(A))
>>Circumference: 2.701769682087222 
>>Area: 0.5808804816487527
```