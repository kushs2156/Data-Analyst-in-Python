Oh you are killing it! Now in this video, I'll introduce the histogram. The histogram is a type of visualisation that's very useful to explore your data. It can help you to get an idea about the distribution of your variables. To see how it works, imagine 12 values between 0 and 6. I've put them along a number line here. To build a histogram for these values, you can divide the line into equal chunks, called bins. Suppose you go for 3 bins, that each have a width of 2. Next, you count how many data points sit inside each bin. There's four data points in the first bin, six in the second bin and 2 in the third bin. Finally, you draw a bar for each bin. The height of the bar corresponds to the number of data points that fall in this bin. The result is a histogram, which gives us a nice overview on how the 12 values are distributed. Most values are in the middle, but there are more values below 2 than there are above 4. Of course, we can use matplotlib to build histograms as well.

As before, you should start by importing the pyplot package that's inside matplotlib. Next, you can use the hist function. Let's open up its documentation. There's a bunch of arguments you can specify, but the first two here are the most important ones. `x` should be a list of values you want to build a histogram for. You can use the second argument, `bins`, to tell Python into how many bins the data should be divided. Based on this number, hist will automatically find appropriate boundaries for all bins, and calculate how may values are in each one. If you don't specify the bins argument, it will by 10 by default.
## Matplotlib example
So to generate the histogram that you've seen before, let's start by building a list with the 12 values. Next, you simply call hist and pass this list as an input, so it's matched to the argument x. I also specified the bins argument to be 3, so that the values are divided in three bins. If you finally call the show function, you get a histogram. 
```Python
values = [0,0.6,1.4,1.6,2.2,2.5,2.6,3.2,3.5,3.9,4.2,6]

plt.hist(values, bins=3)
plt.show()
```
Histograms are really useful to give a bigger picture.
## Let's practice!
Now head over to the exercises to experiment with histograms yourself!