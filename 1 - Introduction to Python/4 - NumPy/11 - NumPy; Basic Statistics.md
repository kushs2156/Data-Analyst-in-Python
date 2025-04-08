A typical first step in analysing your data, is getting to know your data in the first place. For the NumPy arrays from before, this is pretty easy, because it isn't a lot of data. However, as a data scientist, you'll be crunching thousands, if not millions or billions of numbers.
## City-wide survey
Imagine you conduct a city-wide survey where you ask 5000 adults about their height and weight. You end up with something like: a 2D NumPy array, which I named np_city, that has 5000 rows, corresponding to the 5000 people, and two columns, corresponding to the height and the weight. Simply staring at these numbers like a zombie won't give you any insights. What you can do, though, is generate summary statistics about your data.
## NumPy
Aside from an efficient data structure for number crunching, it happens that NumPy is also good at doing these kinds of things. For starters, you can try to find out the average height of these 5000 people, with NumPy's mean function. Because it's a function from the NumPy package, don't forget to start with `np.`. Of course, I first had to do a subsetting operation to get the height column from the 2D array. 
```Python
np.mean(np_city[:, 0])
>>1.7472
```
It appears that on average, people are 1.75 meters tall. What about the median height? This is the height of the middle person if you sort all persons from small to tall. Instead of writing complicated python code to figure this out, you can simply use NumPy's median function: You can do similar things for the weight column in np_city. 
```Python
np.median(np_city[:, 0])
>>1.75
```
Often, these summary statistics will provide you with a "sanity check" of your data. If you end up with a average weight of 2000 kilograms, your measurements are most likely incorrect. 

Apart from mean and median, there's also other functions, like `corrcoeff` to check if for example height and weight are correlated, and `std`, for standard deviation.
```Python
np.corrcoef(np_city[:, 0], np_city[:, 1])
>>array([[ 1.     , -0.01802],
>>       [-0.01803,  1.     ]])

np.std(np_city[:, 0])
>>0.1992
```
NumPy also features more basic functions, such as **sum()** and **sort()**, which also exist in the basic Python distribution. However, the big difference here is speed. Because NumPy enforces a single data type in an array, it can drastically speed up the calculations.
## Generate data
Just a sidenote here: If you're wondering how I came up with the data in this video: We simulated it with NumPy functions! 
```Python
height = np.round(np.random.normal(1.75, 0.20, 5000), 2)
weight = np.round(np.random.normal(60.32, 15, 5000), 2)

np_city = np.column_stack((height, weight))
```
I sampled two random distributions 5000 times to create the height and weight arrays, and then used column_stack to paste them together as two columns. Another awesome thing that NumPy can do! Another great tool to get some sense of your data is to visualise it, but that's something for the next course also.
## Let's practice!
First, head over to the exercise to learn how to explore your NumPy arrays!