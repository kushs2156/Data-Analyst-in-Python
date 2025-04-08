Data scientists commonly use pandas to perform data analysis, so it's a huge advantage that Seaborn works extremely well with pandas data structures. Let's see how this works!
## What is pandas?
pandas is a python library for data analysis. It can easily read datasets from many types of files including csv and txt files. pandas supports several types of data structures, but the most common one is the DataFrame object. When you read in a dataset with pandas, you will create a DataFrame.
## Working with DataFrames
Let's look at an example. First, import the pandas library as "pd". Then, use the `read_csv()` function to read the csv file named "masculinity.csv" and create a pandas DataFrame called "df". Calling `head()` on the DataFrame will show us its first five rows. This dataset contains the results of a survey of adult men. 
```Python
import pandas as pd
df = pd.read_csv("masculinity.csv")
df.head()
```
We can see that it has four columns: "participant_id"; "age"; "how_masculine", which is that person's response to the question "how masculine or 'manly' do you feel?"; and "how_important", which is the response to the question "how important is it to you that others see you as masculine?"
## Using DataFrames with `countplot()`
Now let's look at how to make a count plot with a DataFrame instead of a list of data. The first thing we'll do is import pandas, Matplotlib and Seaborn as we have in past examples. Then, we'll create a pandas DataFrame called "df" from the masculinity.csv file. To create a count plot with a pandas DataFrame column instead of a list of data, set x equal to the name of the column in the DataFrame - in this case, we'll use the "how_masculine" column. Then, we'll set the data parameter equal to our DataFrame, "df". After calling `plt.show()`, we can see that we have a nice count plot of the values in the "how_masculine" column of our data. 
```Python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv("maculinity.csv")
sns.countplot(x="how_masculine", data=df)
plt.show()
```
This plot shows us that the most common response to the question "how masculine or 'manly' do you feel?" is "somewhat", with "very" being the second most common response. Note also that because we're using a named column in the DataFrame, Seaborn automatically adds the name of the column as the x-axis label at the bottom.
## "Tidy" data
Let's pause for an important note here. Seaborn works great with pandas DataFrames, but only if the DataFrame is "tidy". "Tidy data" means that each observation has its own row and each variable has its own column. The "masculinity" DataFrame shown here is tidy because each row is a survey response with one answer to each survey question in each column. Making a count plot with the "how masculine" column works just like passing in a list of that column's values.
## "Untidy" data
In contrast, here is an example of an "untidy" DataFrame made from the same survey on masculinity. In this untidy DataFrame, notice how each row doesn't contain the same information. Row 0 contains the age categories, rows 1 and 7 contain the question text, and the other rows contain summary data of the responses. This will not work well with Seaborn. Unlike the tidy DataFrame, values in the "Age" column don't look like a list of age categories for each observation. Transforming untidy DataFrames into tidy ones is possible, but it's not in scope for this course. There are other DataCamp courses that can teach you how to do this.
## Let's practice!
Now it's time to try out using pandas with Seaborn!