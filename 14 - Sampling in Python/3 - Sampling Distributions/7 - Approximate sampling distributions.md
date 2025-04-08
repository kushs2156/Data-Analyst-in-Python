In the last exercise, we saw that while increasing the number of replicates didn't affect the relative error of the sample means; it did result in a more consistent shape to the distribution.
## 4 dice
Let's consider the case of four six-sided dice rolls. We can generate all possible combinations of rolls using the expand_grid function, which is defined in the pandas documentation, and uses the itertools package. There are six to the power four, or 1296 possible dice roll combinations.
```Python
dice = expand_grid(
	{'die1': [1, 2, 3, 4, 5, 6],
	 'die2': [1, 2, 3, 4, 5, 6],
	 'die3': [1, 2, 3, 4, 5, 6],
	 'die4': [1, 2, 3, 4, 5, 6]
	 }
)
```
Let's consider the mean of the four rolls by adding a column to our DataFrame called mean_roll. mean_roll ranges from 1, when four ones are rolled, to 6, when four sixes are rolled.
```Python
dice['mean_roll'] = (dice['die1'] +
					 dice['die2'] +
					 dice['die3'] +
					 dice['die4']) / 4
print(dice)
```
## Exact sampling distribution
Since the mean roll takes discrete values instead of continuous values, the best way to see the distribution of mean_roll is to draw a bar plot. First, we convert mean_roll to a categorical by setting its type to category. We are interested in the counts of each value, so we use `.value_counts()`, passing the sort equals False argument. This ensures the x-axis ranges from one to six instead of sorting the bars by frequency. Chaining `.plot()` to value_counts, and setting kind to "bar", produces a bar plot of the mean roll distribution. 
```Python
dice['mean_roll'] = dice['mean_roll'].astype('category')
dice['mean_roll'].value_counts(sort=False).plot(kind="bar")
```
This is the exact sampling distribution of the mean roll because it contains every single combination of die rolls.
## The number of outcomes increases fast
If we increase the number of dice in our scenario, the number of possible outcomes increases by a factor of six each time. These values can be shown by creating a DataFrame with two columns: n_dice, ranging from 1 to 100, and n_outcomes, which is the number of possible outcomes, calculated using six to the power of the number of dice. With just one hundred dice, the number of outcomes is about the same as the number of atoms in the universe: six-point-five times ten to the seventy-seventh power. Long before you start dealing with big datasets, it becomes computationally impossible to calculate the exact sampling distribution. That means we need to rely on approximations.
```Python
n_dice = list(range(1, 101))
n_outcomes = []
for n in n_dice:
	n_outcomes.append(6**n)

outcomes = pd.DataFrame(
	{"n_dice": n_dice,
	 "n_outcomes": n_outcomes})

outcomes.plot(x="n_dice", y="n_outcomes", kind="scatter")
plt.show()
```
## Simulating the mean of four dice rolls
We can generate a sample mean of four dice rolls using NumPy's `np.random.choice()` method, specifying size as four. This will randomly choose values from a specified list, in this case, four values from the numbers one to six, which is created using a range from one to seven wrapped in the list function. 
```Python
import numpy as np
sample_means_1000 = []
for i in range(1000):
	sample_means_1000.append(
		np.random.choice(list(range(1, 7)),size=4,replace=True).mean()
	)
print(sample_means_1000)
```
Notice that we set replace equals True because we can roll the same number several times.
Then we use a for loop to generate lots of sample means, in this case, one thousand. We again use the .append method to populate the sample means list with our simulated sample means. The output contains a sampling of many of the same values we saw with the exact sampling distribution.
## Approximate sampling distribution
Here's a histogram of the approximate sampling distribution of mean rolls. This time, it uses the simulated rather than the exact values. It's known as an **approximate sampling distribution**. Notice that although it isn't perfect, it's pretty close to the exact sampling distribution. 
```Python
plt.hist(sample_means_1000, bins=20)
```
Usually, we don't have access to the whole population, so we can't calculate the exact sampling distribution. However, we can feel relatively confident that using an approximation will provide a good guess as to how the sampling distribution will behave.
## Let's practice!
Let's sample some distributions!