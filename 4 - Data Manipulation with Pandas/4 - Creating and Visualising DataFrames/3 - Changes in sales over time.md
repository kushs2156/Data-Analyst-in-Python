- Get the total number of avocados sold on each date. _The DataFrame has two rows for each date—one for organic, and one for conventional_. Save this as `nb_sold_by_date`.
- Create a line plot of the number of avocados sold.
- Show the plot.
```Python
# Import matplotlib.pyplot with alias plt
import matplotlib.pyplot as plt

# Get the total number of avocados sold on each date
nb_sold_by_date = avocados.groupby("date")["nb_sold"].sum()

# Create a line plot of the number of avocados sold by date
nb_sold_by_date.plot(x="date", y="nb_sold", kind="line")

# Show the plot
plt.show()
```
![[download 22.svg]]
