1) Make an HTTP get request to `url`.
```Python
import requests 

url = "http://www.datacamp.com"

r = requests.get(url)

print(type(r))
```
2) Consider the dataset contained in `data.txt` below. Load the file as a single data type object using `numpy`.
```Python
import numpy as np

data = np.loadtxt("data.txt", delimiters="\t", dtype="int")

print(data)
```
3) Load the pickled file `data.pdl` using pandas, then check what type of object was pickled.
```Python
import pandas as pd

x = pd.read_pickle('data.pkl')
print(type(x))
```
4) Consider the Pandas DataFrames `restaurant` and `location` below, respectively. Combine their columns into a single DataFrame.
```Python
import pandas as pd

df = pd.concat([restaurant, location], axis = 1)

print(df)
```
5) A friend sent you an unprocessed `.csv` file containing Data Science skills data that was scraped from a job listing website.
   You're unsure of the structure of the data so import only the first 4 rows to help you decide how to proceed.
```Python
import pandas as pd

job_listings = pd.read_csv(file_name, index_col=0, nrows=4)

print(job_listings.head().transpose())
```
6) Delete the white spaces in the column `name` in Pandas DataFrame `student` shown below.
```Python
import pandas as pd

student['name'] = student['name'].str.strip()

print(student.head())
```
7) Acacia is a large consulting firm and potentially a very large client for your company. Some Acacia employees already use your company's platform. Help determine who these users are by filtering the `users` DataFrame for users that have an '@acacia.com' email address.
```Python
import pandas as pd

print(users[users['email'].str.endswith("@acacia.com")])
```
8) Consider the Pandas `DataFrame` `contact` below. Separate the column `email` by the `@` character.
```Python
print(contact.email.str.split('@', expand = True))
```
9) The data `airquality.csv` is shown below. The headers have not been included in the data. Import the data adding the headers `Day`, `Ozone`, `Temp` and `Wind`, which have been added to a list for you.
```Python
import pandas as pd

cols = ['Day', 'Ozone', 'Temp', 'Wind']

air = pd.read_csv("airquality.csv", names=cols)

print(air)
```
10) Below is a preview of the `wine_sales.csv` data set. For your analysis you only need the columns `style`, `type` and `price`. Import the data, reading only these three columns.
```Python
import pandas as pd

cols = ['style', 'type', 'price']

wine = pd.read_csv(file_name, usecols = cols)

print(wine.head())
```
11) An online games platform would like to assign a special status to their users based on the number of experience points (xp) that users have. The `user_xp` DataFrame contains the `user_ids` and `xp` per user. Use Pandas method to create a new `status` column that indicates a user's special status. The `bins` and `labels` have been defined for you based on the xp status table.
```Python
import pandas as pd

bins = [0, 125000, 250000, 375000, 500000, float('inf')]
labels = ["bronze", "silver", "gold", "platinum", "diamond"]

user_xp['status'] = pd.cut(user_xp['xp'], bins=bins, labels=labels)

print(user_xp.head())
```
12) A friend sent you an unprocessed `.csv` file containing Data Science skills data that was scraped from a job listing website.
   Convert the text in the `roles` column of the `jobs` DataFrame to lower case.
```Python
import pandas as pd

jobs['roles'] = jobs['roles'].str.lower()
print(jobs['roles'].head())
```
13) Determine the data types of all the columns contained in `books` DataFrame.
```Python
print(books.dtypes)
```
14) The `sales` data, previewed below, records the number of items sold by a store on a selection of dates. To be able to perform some date manipulation tasks, convert the `date` column to a `datetime` object.
```Python
import pandas as pd

sales['date'] = pd.to_datetime(sales['date'])

print(sales.head())
```
15) Consider the Pandas DataFrame `df`:
```Python
import pandas as pd

print(df.melt(id_vars = "id", value_vars = ["group_a", "group_b"]))
```