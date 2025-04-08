Write a `for` loop that goes through each key:value pair of `europe`. On each iteration, `"the capital of x is y"` should be printed out, where x is the key and y is the value of the pair.
```Python
# Definition of dictionary
europe = {'spain':'madrid', 'france':'paris', 'germany':'berlin',
          'norway':'oslo', 'italy':'rome', 'poland':'warsaw', 'austria':'vienna' }
# Iterate over europe
for con, city in europe.items():
    print("the capital of " + con + " is " + city)
>>the capital of spain is madrid 
>>the capital of france is paris
>>...
>>the capital of poland is warsaw 
>>the capital of austria is vienna
```
