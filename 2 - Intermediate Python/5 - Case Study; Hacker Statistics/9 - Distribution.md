In this last video of the course, you're ready to learn about the distribution of random walks. Let's go back to the initial problem. you throw a die one hundred times. Depending on the result you go some steps up or some steps down. This is called a random walk, and you know how to simulate this. But you still have to answer the main question: what is the chance that you'll reach 60 steps high? I'll give you a hint. Each random walk will end up on a different step. If you simulate this walk thousands of times, you will end up with thousands of final steps. This is actually a distribution of final steps. And once you know the distribution, you can start calculating chances.

```Python
import numpy as np
np.random.seed(123)
tails = [0]
for x in range(10):
	coin = np.random.randint(0, 2)
	tails.append(tails[x] + coin)
```
Let's go back to the example of the total number of tails after 10 coin tosses. The number of tails starts at zero and, ten times, we calculate a random number which is either 0 or 1. We then update the number of times tails has been thrown by appending it to the list.

```Python
final_tails = []
for x in range(100):
	tails = [0]
	for x in range(10):
		coin = np.random.randint(0, 2)
		tails.append(tails[x] + coin)
	final_tails.append(tails[-1])
print(final_tails)
>>[3, 6, 4, 5, 4, 5, 3, 5, 4, ..., 4]
```
To find the distribution of this walk, we start by setting a random seed, and then create an empty list named final_tails. This list will contain the number of tails you end up with if you play this game of tossing a coin 10 times over and over again. Let's write a for loop that runs 100 times. Inside this for loop, we put the code from before, that gradually builds up the tails list. After simulating this single game, we append the last number, so the number of tails after tossing 10 times, to the final_tails list. Notice that the indentation here specifies that this last line is part of the top-level for loop. If you put a last line in here to print final_tails, outside of the for loops, and run the script, you see that final_tails contains numbers between 0 and 10. Each number is the number of tails that were thrown in a game of 10 tosses. All these values actually represent a distribution, that we can visualise. Hmm, visualising a distribution, that calls for a histogram!

On the top of the script, we add a line to import pyplot, and then, instead of the print statement, we call the hist function, and specify that we want 10 bins. Of course, to actually display the plot, we need plt (dot) show().
```Python
import numpy as np
import matplotlib.pyplot as plt
np.random.seed(123)

final_tails = []
for x in range(100):
	tails = [0]
	for x in range(10):
		coin = np.random.randint(0, 2)
		tails.append(tails[x] + coin)
	final_tails.append(tails[-1])

plt.hist(final_tails, bins=10)
plt.show()
```
If we run the script, the resulting histogram already gives an idea, but is not very smooth yet. Let's head back to the code, and now simulate the coin toss game one thousand times, by changing the range in the top-level for loop. This time, the histogram already looks better. If we change the code to do ten thousand simulations, and run the script once more, the distribution starts to converge to a bell-shape. In fact, it starts to look like the theoretical distribution. That means the distribution that you would find by doing analytical pen-and-paper calculations. Ideally, you want to carry out the experiment zillions of times to get a distribution that is exactly the same as the theoretical distribution. This will take too much computer time, though, but ten thousand already gives a pretty good estimate. From this curve, we can see that in around 2500 games of the 10000 games played, you end up with tails 5 times.
## Let's practice!
In the last exercises of this chapter, you will use a similar technique to simulate the die rolling game in the Empire State Building over and over again. Go out there, and win this thing! And thank you so much for coming on this journey with me. I can't wait to see what you do next with all these skills.