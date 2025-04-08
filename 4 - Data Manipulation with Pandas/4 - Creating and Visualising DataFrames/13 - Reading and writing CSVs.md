You now know how to create your own DataFrames, but typing out your data entry-by-entry isn't usually the most efficient way to get your data into a DataFrame. In this video, you'll learn how to pull data from CSV files.
## What's a CSV file?
CSV, or comma-separated values, is a common data storage file type. It's designed to store tabular data, just like a pandas DataFrame. It's a text file, where each row of data has its own line, and each value is separated by a comma. Almost every database, programming language, and piece of data analysis software can read and write CSV files. That makes it a good storage format if you need to share your data with other people who may be using different tools than you. Remember the dogs from the last video? Their data is stored in a CSV file called new_dogs.csv, which looks like this.
```CSV
name,breed,height_cm,weight_kg,d_o_b
Ginger,Dachshund,22,10,2019-03-14
Scout,Dalmatian,59,25,2019-05-09
```
We can put this data in a DataFrame using the handy pandas function, `read_csv()`, and pass it the file path of the CSV.
```Python
import pandas as pd
new_dogs = pd.read_csv("new_dogs.csv")
```
## DataFrame manipulation
Now that the data is in DataFrame form, we can manipulate it using some of the functions from earlier in the course. Here, we'll add a body mass index column.
```Python
new_dogs["bmi"] = new_dogs["weight_kg"] / 
                  (new_dogs["height_cm"] / 100) ** 2
```
## DataFrame to CSV
Now that we've changed the data let's create an updated CSV file to share with the dogs' owners. To convert a DataFrame to a CSV, we can use:
```Python
new_dogs.to_csv("new_dogs_with_bmi.csv")
```
and pass in a new file path. If we take a look at the new file, it contains the BMI column.
## Let's practice!
Now it's time to practice getting data in and out of pandas!