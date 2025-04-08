- Calculate the quartiles of the `co2_emission` column of `food_consumption`.
- Calculate the six quantiles that split up the data into 5 pieces (quintiles) of the `co2_emission` column of `food_consumption`.
- Calculate the eleven quantiles of `co2_emission` that split up the data into ten pieces (deciles).
```Python
# Calculate the quartiles of co2_emission
print(np.quantile(food_consumption['co2_emission'], 
					np.linspace(0, 1, 5)))
>>[ 0. 5.21 16.53 62.5975 1712. ]
```
```Python
# Calculate the quintiles of co2_emission
print(np.quantile(food_consumption['co2_emission'], 
					np.linspace(0, 1, 6)))
>>[ 0. 3.54 11.026 25.59 99.978 1712. ]
```
```Python
# Calculate the deciles of co2_emission
print(np.quantile(food_consumption['co2_emission'], 
					np.linspace(0, 1, 11)))
>>[0.00000e+00 6.68000e-01 3.54000e+00 7.04000e+00 1.10260e+01            1.65300e+01 2.55900e+01 4.42710e+01 9.99780e+01 2.03629e+02            1.71200e+03]
```