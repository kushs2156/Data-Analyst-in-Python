- Set the color palette to `"Blues"`.
- Add subgroups to color the box plots based on `"Interested in Pets"`.
- Set the title of the `FacetGrid` object `g` to `"Age of Those Interested in Pets vs. Not"`.
- Make the plot display using a Matplotlib function.
```Python
# Set palette to "Blues"
sns.set_palette("Blues")

# Adjust to add subgroups based on "Interested in Pets"
g = sns.catplot(x="Gender",
                y="Age", data=survey_data, 
                kind="box", hue="Interested in Pets")

# Set title to "Age of Those Interested in Pets vs. Not"
g.fig.suptitle("Age of Those Interested in Pets vs. Not")

# Show plot
plt.show()
```
![[download 98.svg]]
