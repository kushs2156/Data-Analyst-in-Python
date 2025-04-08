- Adjust the code to make the box plot whiskers to extend to 0.5 * IQR. Recall: the IQR is the interquartile range.
```Python
# Set the whiskers to 0.5 * IQR
sns.catplot(x="romantic", y="G3", data=student_data,
            kind="box", whis=0.5)

# Show plot
plt.show()
```
![[download 77.svg]]
- Change the code to set the whiskers to extend to the 5th and 95th percentiles.
```Python
# Extend the whiskers to the 5th and 95th percentile
sns.catplot(x="romantic", y="G3", data=student_data,
            kind="box", whis=[5, 95])
            
# Show plot
plt.show()
```
![[download 78.svg]]
- Change the code to set the whiskers to extend to the min and max values.
```Python
# Set the whiskers at the min and max values
sns.catplot(x="romantic", y="G3", data=student_data,
            kind="box", whis=[0, 100])

# Show plot
plt.show()
```
![[download 79.svg]]
