- Use chained square brackets to select and print out the capital of France.
- Create a dictionary, named `data`, with the keys `'capital'` and `'population'`. Set them to `'rome'` and `59.83`, respectively.
- Add a new key-value pair to `europe`; the key is `'italy'` and the value is `data`, the dictionary you just built.
```Python
# Dictionary of dictionaries
europe = { 'spain': { 'capital':'madrid', 'population':46.77 },
           'france': { 'capital':'paris', 'population':66.03 },
           'germany': { 'capital':'berlin', 'population':80.62 },
           'norway': { 'capital':'oslo', 'population':5.084 } }

# Print out the capital of France
print(europe["france"]["population"])
>>66.03

# Create sub-dictionary data
data = {"capital":"rome", "population":59.83}

# Add data to europe under key 'italy'
europe["italy"] = data

# Print europe
print(europe)
>>{'spain': {'capital': 'madrid', 'population': 46.77}, 
>>'france': {'capital': 'paris', 'population': 66.03}, 
>>'germany': {'capital': 'berlin', 'population': 80.62}, 
>>'norway': {'capital': 'oslo', 'population': 5.084}, 
>>'italy': {'capital': 'rome', 'population': 59.83}}
```