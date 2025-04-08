So far we've covered how to create a variety of different plot types. Now let's learn how to customise them.
## Why customise?
By default, Seaborn plots are pleasing to look at, but there are several reasons you may want to change the appearance. Changing the style of a plot can be motivated by personal preference, but it can also help improve its readability or help orient an audience more quickly to the key takeaway.
## Changing the figure style
Seaborn has five pre-set figure styles which change the background and axes of the plot. You can refer to them by name: "white", "dark", "whitegrid", "darkgrid", and "ticks". To set one of these as the global style for all of your plots, use the "set style" function, `sns.set_style()`.
## Default figure style ("white")
This is a plot we've seen before, showing the percentage of men reporting that masculinity was important to them, stratified by their age and whether or not they feel masculine. The default style is called "white" and provides clean axes with a solid white background. If we only care about the comparisons between groups or the general trend across age groups instead of the specific values, this is a good choice.
## Figure style: "whitegrid"
Changing the style to "whitegrid" will add a gray grid in the background. This is useful if you want your audience to be able to determine the specific values of the plotted points instead of making higher level observations.
```Python
sns.set_style("whitegrid")

sns.catplot(x="age", y="masculinity_important",
			data=masculinity_data, hue="feel_masculine",
			kind="point")
plt.show()
```
## Other styles
The other styles are variants on these. "ticks" is similar to "white", but adds small tick marks to the x- and y-axes. "dark" provides a grey background, and "darkgrid" provides a grey background with a white grid.
## Changing the palette
You can change the colour of the main elements of the plot with Seaborn's `sns.set_palette()` function. Seaborn has many pre-set colour palettes that you can refer to by name, or you can create your own custom palette. Let's see an example.
## Diverging palettes
Seaborn has a group of pre-set palettes called diverging palettes that are great to use if your visualisation deals with a scale where the two ends of the scale are opposites and there is a neutral midpoint. Here are some examples of diverging palettes - red/blue ("RdBu") and purple/green ("PRGn"). Note that if you append the palette name with "\_r", you can reverse the palette. To see this in action, let's return to a count plot we've seen before of the responses of men reporting how masculine they feel. Setting this plot's palette to red/blue diverging provides a clearer contrast between the men who do not feel masculine and the men who do.
```Python
sns.set_palette("RdBu")

category_order = ["No answer", "Not at all", "Not very",
				  "Somewhat", "Very"]

sns.catplot(x="how_masculine", data=masculinity_data,
			kind="count", order=category_order)
plt.show()
```
## Sequential palettes
Another group of palettes are called sequential palettes. These are a single colour (or two colours blended) moving from light to dark values ("Greys", "Blues", "PuRd", "GnBu"). Sequential palettes are great for emphasising a variable on a continuous scale. One example is this plot depicting the relationship between a car's horsepower and its miles per gallon, where points grow larger and darker when the car has more cylinders.
## Custom palettes
You can also create your own custom palettes by passing in a list of colour names or a list of hex colour codes.
```Python
custom_palette = ["red", "green", "orange", "blue",
				  "yellow", "purple"]
sns.set_palette(custom_palette)

customer_palette = ['#FBB4AE', '#B3CDE3', '#CCEBC5',
					'#DECBE4', '#FED9A6', '#FFFFCC',
					'#E5D8BD', '#FDDAEC', '#F2F2F2']
sns.set_palette(custom_palette)
```
## Changing the scale
Finally, you can change the scale of your plot by using the `sns.set_context()` function. The scale options from smallest to largest are "paper", "notebook", "talk", and "poster". The default context is "paper". You'll want to choose a larger scale like "talk" for posters or presentations where the audience is further away from the plot.
## Let's practice!
Now that we've seen how to change the plot style, palette, and scale, let's practice!