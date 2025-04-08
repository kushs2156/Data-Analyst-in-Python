- Create a KDE plot that shows `marriage_duration` on the x-axis and a different colored line for each possible number of children that a couple might have, represented by `num_kids`.
```Python
# Create the KDE plot
sns.kdeplot(data=divorce, x="marriage_duration", hue="num_kids")
plt.show()
```
![[download 111.svg]]
- Notice that the plot currently shows marriage durations less than zero; update the KDE plot so that marriage duration cannot be smoothed past the extreme data points.
```Python
# Update the KDE plot so that marriage duration can't be smoothed too far
sns.kdeplot(data=divorce, x="marriage_duration", hue="num_kids", cut=0)
plt.show()
```
![[download 112.svg]]
- Update the code for the KDE plot from the previous step to show a cumulative distribution function for each number of children a couple has.
```Python
# Update the KDE plot to show a cumulative distribution function
sns.kdeplot(data=divorce, x="marriage_duration", hue="num_kids", 
			cut=0, cumulative=True)
plt.show()
```
![[download 113.svg]]
