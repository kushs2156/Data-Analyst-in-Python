1) Return the `food` DataFrame, previewed below, sorted by the index value `item` in descending order.
```Python
print(food.sort_index(level = 'item', ascending=False))
```
2) The `chess` DataFrame contains information about the top female chess players around the world. A preview of the DataFrame is shown. Set the index of the DataFrame to be the column containing the `id` of the players.
```Python
print(food.sort_index(level = 'item', ascending=False))
```
3) Calculate the inter-quartile range of the `age` of 100 customers who have recently bought products from your website.
```Python
import pandas as pd

Q1 = df['age'].quantile(0.25)
Q3 = df['age'].quantile(0.75)

print(Q3 - Q1)
```
4) Following a trial of a new treatment, you wish to create a plot of the change over the time of the trial (`week`) of the patient response (`resp`). The `patient` data is shown below.
```Python
import matplotlib.pyplot as plt
import seaborn as sns

sns.lineplot(x = "week", y = "resp", data = patient)

plt.show()
```
5) You have `sales` data for the years 2018 and 2019. Create a new DataFrame, `sales_2019`, that contains data from 2019 only.
```Python
sales_2019 = sales[sales["Year"] == 2019]

print(sales_2019.head())
```
6) Create a `scatterplot` of `mpg` vs `age` and colour it based on the `emissions` categorical variable.
```Python
import matplotlib.pyplot as plt
import seaborn as sns

ax = sns.scatterplot(x="age", y="mpg", hue="emissions",
					 data=valuation)

plt.show()
```
7) Two of the columns in the `heart` DataFrame have very long names. Rename the columns using the provided `dictionary`.
```Python
import pandas as pd

column_names = {
		'slope_of_peak_exercise_st_segment': 'slope',
		'fasting_blood_sugar_gt_120_mg_per_dl': 'fbs'
}

heart_clean = heart.rename(columns=column_names)
print(heart_clean.head())
```
8) Calculate the inter-quartile range of the `age` of 100 customers who have recently bought products from your website. `age` is a NumPy array.
```Python
from scipy import stats

iqr_age = stats.iqr(age)

print(iqr_age)
```
9) Create a swarm plot of `value` as a function of `measurement`. Use the colour to indicate the `species`. The data is contained in the `iris` DataFrame.
```Python
import matplotlib.pyplot as plt
import seaborn as sns

ax = sns.swarmplot(x="measurement", y="value", hue="species",
				   data=iris)

plt.show()
```
10) In preparation for an upcoming staffing review, your manager has asked you to sort the records of `employee` DataFrame by `gender` alphabetically, and then by salaries in descending order.
```Python
employee_sorted = employee.sort_values(['gender', 'salary'], 
						ascending=[True, False])
```
11) Plot the monthly dam level height contained in the `dam_level` DataFrame.
```Python
import matplotlib.pyplot as plt
import seaborn as sns

sns.lineplot(x="date", y="level", data=dam_level)

plt.xticks(rotation=45)
plt.show()
```
12) Create a bar plot of the data contained in the `df` Pandas DataFrame.
```Python
import matplotlib.pyplot as plt
import seaborn as sns

ax = sns.barplot(x="Grade", y="Count", data=df)

plt.show()
```
13) Using the `food` DataFrame, previewed below, print the row for the `item` with the largest amount of `energy` per 100g.
```Python
largest = food[food['energy'] == food['energy'].max()]

print(largest)
```
14) Complete the code to return the output.
```Python
import pandas as pd

print(pd.DataFrame({'x': ['a', 'b']}, index = [0, 1]))
```
15) For each `profession` with the same `sex` in the DataFrame `df`, calculate the mean weight and height.
```Python
import numpy as np

print(df.groupby(['profession', 'sex'])[['weight_kg', 'height_cm']].mean())
```