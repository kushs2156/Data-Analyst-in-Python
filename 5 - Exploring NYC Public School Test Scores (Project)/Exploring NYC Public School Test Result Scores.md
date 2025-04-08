Which NYC schools have the best math results?

- The best math results are at least 80% of the ***maximum possible score of 800*** for math.
- Save your results in a pandas DataFrame called `best_math_schools`, including `"school_name"` and `"average_math"` columns, sorted by `"average_math"` in descending order.

What are the top 10 performing schools based on the combined SAT scores?

- Save your results as a pandas DataFrame called `top_10_schools` containing the `"school_name"` and a new column named `"total_SAT"`, with results ordered by `"total_SAT"` in descending order (`"total_SAT"` being the sum of math, reading, and writing scores).

Which single borough has the largest standard deviation in the combined SAT score?

- Save your results as a pandas DataFrame called `largest_std_dev`.
- The DataFrame should contain one row, with:
    - `"borough"` - the name of the NYC borough with the largest standard deviation of `"total_SAT"`.
    - `"num_schools"` - the number of schools in the borough.
    - `"average_SAT"` - the mean of `"total_SAT"`.
    - `"std_SAT"` - the standard deviation of `"total_SAT"`.
- Round all numeric values to two decimal places.
  

Every year, American high school students take SATs, which are standardized tests intended to measure literacy, numeracy, and writing skills. There are three sections - reading, math, and writing, each with a **maximum score of 800 points**. These tests are extremely important for students and colleges, as they play a pivotal role in the admissions process.

Analysing the performance of schools is important for a variety of stakeholders, including policy and education professionals, researchers, government, and even parents considering which school their children should attend.

You have been provided with a dataset called `schools.csv`, which is previewed below.

You have been tasked with answering three key questions about New York City (NYC) public school SAT performance.
```Python
# Re-run this cell 
import pandas as pd

# Read in the data
schools = pd.read_csv("schools.csv")

# Preview the data
schools.head()

# Start coding here...
# Add as many cells as you like...
```
```Python
# Which schools are best for math?
best_math_schools = schools[schools["average_math"] >= (0.8 * 800)][["school_name", "average_math"]].sort_values("average_math", ascending=False)
```
```Python
# Calculate total_SAT per school
schools["total_SAT"] = schools["average_math"] + schools["average_reading"] + schools["average_writing"]

# Who are the top 10 performing schools?
top_10_schools = schools[["school_name", "total_SAT"]].sort_values("total_SAT", ascending=False).head(10)
```
```Python
# Which NYC borough has the highest standard deviation for total_SAT?
boroughs = schools.groupby("borough")["total_SAT"].agg(["count", "mean", "std"]).round(2)

# Filter for max std and make borough a column
largest_std_dev = boroughs[boroughs["std"] == boroughs["std"].max()]

# Rename the columns for clarity
largest_std_dev = largest_std_dev.rename(columns={"count": "num_schools", "mean": "average_SAT", "std": "std_SAT"})

# Optional: Move borough from index to column
largest_std_dev.reset_index(inplace=True)
```

