- Using the iterators `lab` and `row`, adapt the code in the for loop such that the first iteration prints out `"US: 809"`, the second iteration `"AUS: 731"`, and so on.
- The output should be in the form `"country: cars_per_cap"`. Make sure to print out this exact string (with the correct spacing).
    - _You can use `str()` to convert your integer data to a string so that you can print it in conjunction with the country label._
```Python
# Import cars data
import pandas as pd
cars = pd.read_csv('cars.csv', index_col = 0)

# Adapt for loop
for lab, row in cars.iterrows() :
    print(lab + ": " + str(row["cars_per_cap"]))
>>US: 809 
>>AUS: 731 
>>JPN: 588 
>>IN: 18 
>>RU: 200 
>>MOR: 70 
>>EG: 45
```
