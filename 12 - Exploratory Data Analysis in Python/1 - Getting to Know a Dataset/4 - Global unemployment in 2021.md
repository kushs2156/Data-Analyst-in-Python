- Import the required visualization libraries.
- Create a histogram of the distribution of 2021 unemployment percentages across all countries in `unemployment`; show a full percentage point in each bin.
```Python
# Import the required visualization libraries
import seaborn as sns
import matplotlib.pyplot as plt

# Create a histogram of 2021 unemployment; show a full percent in each bin
sns.histplot(data=unemployment, x="2021", binwidth=1)
plt.show()
```
![[download 100.svg]]
