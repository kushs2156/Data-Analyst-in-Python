In the last lesson, you saw how to subset and sort a DataFrame to extract interesting bits. However, often when you first receive a DataFrame, the contents aren't exactly what you want. You may have to add new columns derived from existing columns.

Creating and adding new columns can go by many names, including **mutating** a DataFrame, **transforming** a DataFrame, and **feature engineering**. Let's say we want to add a new column to our DataFrame that has each dog's height in meters instead of centimetres. On the left-hand side of the equality, we use square brackets with the name of the new column we want to create. On the right-hand side, we have the calculation. Notice that both the existing column and the new column we just created are in the DataFrame.
```Python
dogs["height_m"] = dogs["height_cm"] / 100
```

Let's see what the results are if we calculate the body mass index, or BMI, of these dogs. BMI is usually calculated by taking a person's weight in kilograms and dividing it by their height in meters, squared. Instead of doing this with people, we'll try it out with dogs. Again, the new column is on the left-hand side of the equals, but this time, our calculation involves two columns.
```Python
dogs["bmi"] = dogs["weight_kg"] / dogs["height_m"] ** 2
```
## Multiple manipulations
The real power of pandas comes in when you combine all the skills you've learned so far. Let's figure out the names of skinny, tall dogs. First, to define the skinny dogs, we take the subset of the dogs who have a BMI of under 100. Next, we sort the result in descending order of height to get the tallest skinny dogs at the top. Finally, we keep only the columns we're interested in. Here, you can see that Max is the tallest dog with a BMI of under 100.
```Python
bmi_lt_100 = dogs[dogs["bmi"] < 100]
bmi_lt_100_height = bmi_lt_100.sort_values("height_cm", ascending=False)
bmi_lt_100_height[["name", "height_cm", "bmi"]]
```
## Let's practice!
Time to practice your pandas powers!