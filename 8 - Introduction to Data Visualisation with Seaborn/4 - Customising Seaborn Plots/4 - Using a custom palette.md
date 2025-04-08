- Set the style to `"darkgrid"`.
- Set a custom colour palette with the hex colour codes `"#39A7D0"` and `"#36ADA4"`.
```Python
# Set the style to "darkgrid"
sns.set_style("darkgrid")

# Set a custom color palette
sns.set_palette(['#39A7D0', '#36ADA4'])

# Create the box plot of age distribution by gender
sns.catplot(x="Gender", y="Age", 
            data=survey_data, kind="box")
            
# Show plot
plt.show()
```
![[download 93.svg]]
