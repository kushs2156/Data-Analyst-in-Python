Now that you've learned a lot about how to work with pandas DataFrames, how do you get data into a DataFrame in the first place?
## Dictionaries
Before creating your own DataFrames, let's talk about dictionaries. A dictionary is a way of storing data in Python. It holds a set of key-value pairs. You can create a dictionary like this, using curly braces. 
```Python
my_dict = {
		   "key1": value1,
		   "key2": value2,
		   "key3": value3
}
```
Inside, each key-value pair is written as `key:value`. Let's create a dictionary that holds information about a book. "Title" is a key in the dictionary, and "Charlotte's Web" is its corresponding value, and so on. You can access values of a dictionary via their keys in square brackets. For example, we can access the value of "title" like this.
```Python
my_dict = {
		   "title": "Charlotte's Web",
		   "author": "E.B. White",
		   "published": 1952
}

my_dict["title"]
>>Charlotte's Web
```

There are many ways to create DataFrames from scratch, but we'll discuss two ways: from a list of dictionaries and from a dictionary of lists. In the first method, the DataFrame is built up row by row, while in the second method, the DataFrame is built up column by column.

| List of dictionaries   | Dictionary of lists          |
| ---------------------- | ---------------------------- |
| Constructed row by row | Constructed column by column |
## List of dictionaries - by row
We have some new dog data to put into a DataFrame. Let's start with the first method to do this, creating a list of dictionaries. First, we'll create a new list using square brackets to hold our dictionaries. Then, we'll go through the first row of our data and put it in a dictionary. Each key, on the left of each colon, will become a column name. Each value is one dog's data for that column. 
```Python
list_of_dicts = [
		{"name": "Ginger", "breed": "Dachshund", "height_cm": 22,
		 "weight_kg": 10, "date_of_birth": "2019-03-14"},
		{"name": "Scout", "breed": "Dalmatian", "height_cm": 59,
		 "weight_kg": 25, "date_of_birth": "2019-05-09"}		 
]

new_dogs = pd.DataFrame(list_of_dicts)
```
Here, the first key is "name," which is the first column name, and its corresponding value is "Ginger," the name of the first dog. The second key is the second column name, "breed," and its value is "Dachshund," which is the first dog's breed. Then we have the dog's height and weight. For the next row, we create another dictionary that follows the same format.
## Dictionary of lists - by column
Now let's talk about the dictionary of lists method. When using this method, we need to go through the data column by column. Remember that keys are to the left of a colon, and values are to the right. Each key will be a column name, and each value will be a list of the values in the column. First, we'll create a dictionary using curly braces. Let's start with the first column, which is called "name," so the first key is "name." The value is a list containing each name, from top to bottom. 
```Python
dict_of_lists = {
				 "name": ["Ginger", "Scout"],
				 "breed": ["Dachshund", "Dalmatian"],
				 "height_cm": [22, 59],
				 "weight_kg": [10, 25],
				 "date_of_birth": ["2019-03-14", "2019-05-09"]
}

new_dogs = pd.DataFrame(dict_of_lists)
```
In this case, it's "Ginger" and "Scout." Next, we have the "breed" column, so we add "breed" as a key, and its corresponding value is a list containing "Dachshund" and "Dalmatian." Then we have height_cm, which is 22 and 59, and weight_kg, which is 10 and 25. Now that we have our dictionary of lists set up, we can pass it into pd-dot-DataFrame to convert it into a pandas DataFrame. If we print the new DataFrame, we can see that it's exactly what we wanted.
## Let's practice!
Time to practice creating your own DataFrames!