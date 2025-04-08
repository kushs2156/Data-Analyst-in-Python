So far, in this chapter, you've learned how to summarise numeric variables. In this video, you'll learn how to summarise categorical data using counting.
## Avoiding double counting
Counting dogs is no easy task when they're running around the park. It's hard to keep track of who you have and haven't counted! Here's a DataFrame that contains vet visits. The vet's office wants to know how many dogs of each breed have visited their office. However, some dogs have been to the vet more than once, like Max and Stella, so we can't just count the number of each breed in the breed column.

Let's try to fix this by removing rows that contain a dog name already listed earlier in the dataset, or in other words; we'll extract a dog with each name from the dataset once. We can do this using the `.drop_duplicates()` method. It takes an argument, subset, which is the column we want to find our duplicates based on - in this case, we want all the unique names. 
```Python
vet_visits.drop_duplicates(subset="name")
```
Now we have a list of dogs where each one appears once. We have Max the Chow Chow, but where did Max the Labrador go? Because we have two different dogs with the same name, we'll need to consider more than just name when dropping duplicates.

Since Max and Max are different breeds, we can drop the rows with pairs of name and breed listed earlier in the dataset. To base our duplicate dropping on multiple columns, we can pass a list of column names to the subset argument, in this case, name and breed. Now both Maxes have been included, and we can start counting.
```Python
vet_visits.drop_duplicates(subset=["name", "breed"])
```
## Easy as 1, 2, 3
To count the dogs of each breed, we'll subset the breed column and use the value_counts method. We can also use the sort argument to get the breeds with the biggest counts on top.
```Python
unique_dogs["breed"].value_counts()

unique_dogs["breed"].value_counts(sort=True)

unique_dogs["breed"].value_counts(normalize=True)
```
The normalize argument can be used to turn the counts into proportions of the total. 25% of the dogs that go to this vet are Labradors.
## Let's practice!
Time to commence counting!
