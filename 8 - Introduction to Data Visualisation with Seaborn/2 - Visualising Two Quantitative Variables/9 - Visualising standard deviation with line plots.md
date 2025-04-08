- Change the plot so the shaded area shows the standard deviation instead of the confidence interval for the mean.
```Python
# Make the shaded area show the standard deviation
sns.relplot(x="model_year", y="mpg",
            data=mpg, kind="line", ci="sd")

# Show plot
plt.show()
```
![[download 64.svg]]
