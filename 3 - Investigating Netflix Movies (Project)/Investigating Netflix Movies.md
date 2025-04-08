Perform exploratory data analysis on the `netflix_data.csv` data to understand more about movies from the 1990s decade.

- What was the most frequent **movie** duration in the 1990s? Save an approximate answer as an integer called `duration` (use 1990 as the decade's start year).
    
- A movie is considered short if it is less than 90 minutes. Count the number of **short action movies** released in the 1990s and save this integer as `short_movie_count`.
    

Feel free to experiment after submitting the project!

**Netflix**! What started in 1997 as a DVD rental service has since exploded into one of the largest entertainment and media companies.

Given the large number of movies and series available on the platform, it is a perfect opportunity to flex your exploratory data analysis skills and dive into the entertainment industry.

You work for a production company that specializes in nostalgic styles. You want to do some research on movies released in the 1990's. You'll delve into Netflix data and perform exploratory data analysis to better understand this awesome movie decade!

You have been supplied with the dataset `netflix_data.csv`, along with the following table detailing the column names and descriptions. Feel free to experiment further after submitting!

### The data

**netflix_data.csv**

|Column|Description|
|---|---|
|`show_id`|The ID of the show|
|`type`|Type of show|
|`title`|Title of the show|
|`director`|Director of the show|
|`cast`|Cast of the show|
|`country`|Country of origin|
|`date_added`|Date added to Netflix|
|`release_year`|Year of Netflix release|
|`duration`|Duration of the show in minutes|
|`description`|Description of the show|
|`genre`|Show genre|
```Python
# Importing pandas and matplotlib
import pandas as pd
import matplotlib.pyplot as plt

# Read in the Netflix CSV as a DataFrame
netflix_df = pd.read_csv("netflix_data.csv")
```
```Python
mov_1990s = netflix_df[(netflix_df["release_year"] >= 1990) & (netflix_df["release_year"] < 2000)]
```
```Python
plt.hist(mov_1990s["duration"], bins=20)
```
![[Pasted image 20250119225356.png]]
```Python
duration = 101
```
```Python
short_movie_count = mov_1990s[(mov_1990s["duration"] < 90) & (mov_1990s["genre"] == "Action")]["genre"].count()
```
```Python
short_movie_count
>>7
```
