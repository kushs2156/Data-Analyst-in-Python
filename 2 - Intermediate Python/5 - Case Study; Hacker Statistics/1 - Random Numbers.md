Well done and you're on the home stretch now! This chapter will be a bit different from the others. Step by step, we're going to work towards a cool script, using everything we've learned during this course.

Imagine the following: you're walking up the empire state building to DataCamp Head Quarters and you're playing a game with a friend. You throw a die one hundred times. If it's 1 or 2 you'll go one step down. If it's 3, 4, or 5, you'll go one step up. If you throw a 6, you'll throw the die again and will walk up the resulting number of steps. Of course, you can not go lower than step number 0. And also, you admit that you're a bit clumsy and have a chance of 0.1% of falling down the stairs when you make a move. Falling down means that you have to start again from step 0. With all of this in mind, you bet with your friend that you'll reach 60 steps high.

What is the chance that you will win this bet? It's a complex assignment. One way to solve it would be to calculate the chance analytically using equations. Another possible approach, is to simulate this process thousands of times, and see in what fraction of the simulations that you will reach 60 steps. This is a form of **hacker statistics**. As you can probably guess, we're going to opt for the second approach.
## Random generators
The first thing we'll need are random generators, so we can simulate the die. You need to import NumPy, and inside NumPy, there is the random package. Inside that package we find the `rand()` function. Let's try it out: we get a random number between zero and one. How was this random number created? Well, computers typically generate so-called pseudo-random numbers. Those are random numbers that are generated using a mathematical formula, starting from a random seed. This seed was chosen by Python when we called the rand function, but you can also set this manually. Suppose we set it to 123, just a number I chose, like this, and then call the rand function twice. We get two random numbers. Now, if I set the seed back to 123, and call rand twice more, we get the exact same random numbers. 
```Python
import numpy as np
np.random.rand() # Pseudo-random numbers
>>0.9535543896720104 # Mathematical formula

np.random.seed(123)
np.random.rand()
>>0.696469185597861
np.random.rand()
>>0.28613933495037946

np.random.seed(123)
np.random.rand()
>>0.696469185597861 # Same seed: same random numbers!
np.random.rand() # Ensures "reproducibility"
>>0.28613933495037946
```
This is funky: you're generating random numbers, but for the same seed, you're generating the same random numbers. That's why it's called pseudo-random; it's random but consistent between runs; this is very useful, because this ensures "reproducibility". Other people can reproduce your analysis. Let's use this randomness in a new example now.
## Coin toss
Suppose we want to simulate a coin toss. First set the seed - again, this could be anything - and then use the randint() function. To have it randomly generate either 0 or 1, we pass two arguments: the first argument should be 0, the second one 2, because 2 is not going to be included. If we print out coin, and then run the script, we get a random integer, 0. You can now use this coin to play a game.
```Python
import numpy as np
np.random.seed(123)
coin = np.random.randint(0,2) # Randomly generate 0 or 1
print(coin)

if coin == 0:
	print("heads")
else:
	print("tails")
>>0
>>heads
```
We extend the code with an if-else statement: if coin equals 0, we print out "heads". If it equals 1, we print out "tails". If we now run this script again, coin will again equal 0, because the seed is the same. This also means that the if condition is True, so the string heads is printed out. This was a first example on how you can use random numbers to simulate real life situations that involve chance, or probability.
## Let's practice!
Now head over to the exercises and start to code your Empire State Building simulation!