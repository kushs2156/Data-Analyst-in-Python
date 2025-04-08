Hypothesis tests are like criminal trials. There are two possible true states: the defendant either committed the crime, or didn't. There are also two possible outcomes: a guilty or not guilty verdict. The initial assumption is that the defendant is not guilty, and the prosecution team must present evidence beyond a reasonable doubt that the defendant committed the crime for a guilty verdict to be given.
## Age of first programming experience
Let's return to the Stack Overflow survey. The `age_first_code_cut` variable classifies when the user began programming. If they were 14 or older, they are classified as adult; otherwise, child. Suppose previous research suggests that 35% of software developers programmed as children. This raises a question answerable with our dataset. Does our sample provide evidence that a greater proportion of data scientists started programming as children?
## Definitions
Let's specify some definitions. A hypothesis is a statement about a population parameter. We don't know the true value of this population parameter; we can only make inferences about it from the data. Hypothesis tests compare two competing hypotheses. These two hypotheses are the null hypothesis, representing the existing idea, and the alternative hypothesis, representing a new idea that challenges the existing one. They are denoted $H_0$ and $H_A$, respectively. Here, the null hypothesis is that the proportion of data scientists that started programming as children follows the research on software developers, at 35%. The alternative hypothesis is that the percentage is greater than 35.
## Criminal trials vs. hypothesis testing
Returning to our criminal trial comparison, the defendant can be either guilty or not guilty, and likewise, only one of the hypotheses can be true. Initially, the defendant is assumed to be not guilty and, similarly, we initially assume that the null hypothesis is true. This only changes if the sample provides enough evidence to reject it. Rather than saying we accept the alternative hypothesis, it is convention to refer to rejecting the null hypothesis, or failing to reject the null hypothesis. If the evidence is "beyond a reasonable doubt" that the defendant committed the crime, then a "guilty" verdict is given. The hypothesis testing equivalent of "beyond a reasonable doubt" is known as the significance level - more on this later in the chapter.
## One-tailed and two-tailed tests
The tails of a distribution are the left and right edges of its PDF. Hypothesis tests determine whether the sample statistics lie in the tails of the null distribution, which is the distribution of the statistic if the null hypothesis was true. There are three types of tests, and the phrasing of the alternative hypothesis determines which type we should use. If we are checking for a difference compared to a hypothesised value, we look for extreme values in either tail and perform a two-tailed test. If the alternative hypothesis uses language like "less" or "fewer", we perform a left-tailed test. Words like "greater" or "exceeds" correspond to a right-tailed test. For the Stack Overflow hypothesis test, we need a right-tailed test since we are looking for extreme values in the right tail.

| Test                              | Tails        |
| --------------------------------- | ------------ |
| alternative *different from null* | two-tailed   |
| alternative *greater than null*   | right-tailed |
| alternative *less than null*      | left-tailed  |
## p-values
p-values measure the strength of support for the null hypothesis, or in other words, they measure the probability of obtaining a result, assuming the null hypothesis is true. Large p-values mean our statistic is producing a result that is likely not in a tail of our null distribution, and chance could be a good explanation for the result. Small p-values mean our statistic is producing a result likely in the tail of our null distribution. Because p-values are probabilities, they are always between zero and one.
## Calculating the z-score
To calculate the p-value, we must first calculate the z-score. We calculate the sample statistic, in this case the proportion of data scientists who started programming as children. The hypothesised value from the null hypothesis is 35%. We get the standard error from the standard deviation of the bootstrap distribution, and the z-score is the difference between the proportions, divided by the standard error.
```Python
prop_child_samp = (stack_overflow['age_first_code_cut'] == 'child')\
	.mean()
>>0.39141972578505085

prop_child_hyp = 0.35

std_error = np.std(first_code_boot_distn, ddof=1)
>>0.010351057228878566

z_score = (prop_child_samp - prop_child_hyp) / std_error
>>4.001497129152506
```
We pass the z-score to the standard normal CDF, norm.cdf, from scipy.stats with the default values of mean zero and standard deviation of one. As we're performing a right-tail test, not a left-tail test, the p-value is calculated by taking one minus the norm.cdf result. The p-value is 3 out of 100,000.
```Python
from scipy.stats import norm
1 - norm.cdf(z_score, loc=0, scale=1)
>>3.1471479512323874e-0.5
```
## Let's practice!
Go calculate some p-values!