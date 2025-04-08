- Set the figure style to `"dark"`.
- Adjust the bar plot code to add subplots based on `"Gender"`, arranged in columns.
- Add the title `"Percentage of Young People Who Like Techno"` to this `FacetGrid` plot.
- Label the x-axis `"Location of Residence"` and y-axis `"% Who Like Techno"`.
```Python
# Set the figure style to "dark"
sns.set_style("dark")

# Adjust to add subplots per gender
g = sns.catplot(x="Village - town", y="Likes Techno", 
                data=survey_data, kind="bar",
                col="Gender")

# Add title and axis labels
g.fig.suptitle("Percentage of Young People Who Like Techno", y=1.02)
g.set(xlabel="Location of Residence", 
      ylabel="% Who Like Techno")

# Show plot
plt.show()
```
![[download 99.svg]]
