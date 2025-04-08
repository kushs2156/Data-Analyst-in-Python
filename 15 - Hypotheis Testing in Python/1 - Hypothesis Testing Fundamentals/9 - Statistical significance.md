Last time, we introduced p-values. p-values quantify how much evidence there is for the null hypothesis. Large p-values indicate a lack of evidence for the alternative hypothesis, sticking with the assumed null hypothesis instead. Small p-values make us doubt this original assumption in favour of the alternative hypothesis. What defines the cut-off point between a small p-value and a large one?
## Significance level
The cut-off point is known as the significance level, and is denoted alpha ($\alpha$). The appropriate significance level depends on the dataset and the discipline worked in. 5% is the most common choice, but 10% and 1% are also popular. The significance level gives us a decision process for which hypothesis to support. If the p-value is less than or equal to alpha, we reject the null hypothesis. Otherwise, we fail to reject it. It's important that we decide what the appropriate significance level should be before we run our test. Otherwise, there is a temptation to decide on a significance level that lets us choose the hypothesis we want.
## Calculating the p-value
The workflow starts with setting the significance level, in this case 0.05. Next, we calculate the sample mean and assign the hypothesised mean. For the z-score, we also need the standard error, which we obtain from the bootstrap distribution. Then we calculate the z-score using the sample mean, hypothesised mean, and standard error, and use the standard normal CDF to get the p-value. In this case, the p-value of $3\times10^{-5}$ is less than or equal to 0.05, so we reject the null hypothesis. We have strong evidence for the alternative hypothesis that the proportion of data scientists that started programming as children is greater than 35%.
## Confidence intervals
To get a sense of the potential values of the population parameter, it's common to choose a confidence interval level of one minus the significance level. For a significance level of 0.05, we'd use a 95% confidence interval. Here's the calculation using the quantile method. The interval provides a range of plausible values for the population proportion of data scientists that programmed as children.
```Python
import numpy as np
lower = np.quantile(first_code_boot_distn, 0.025)
upper = np.quantile(first_code_boot_distn, 0.075)
print((lower, upper))
>>(0.37063246351172047, 0.41132242370632466)
```
## Types of errors
Returning to the criminal trial analogy, there are two possible truth states and two possible test outcomes, amounting to four combinations. Two of these indicate that the verdict was correct. If the defendant didn't commit the crime, but the verdict was guilty, they are wrongfully convicted. If the defendant committed the crime, but the verdict was not guilty, they got away with it. These are both errors in justice. Similarly, for hypothesis testing, there are two ways to get it right, and two types of error. If we support the alternative hypothesis when the null hypothesis was correct, we made a false positive error. If we support the null hypothesis when the alternative hypothesis was correct, we made a false negative error. These errors are sometimes known as type one and type two errors, respectively.

|                  | actual $H_0$               | actual $H_A$                |
| ---------------- | -------------------------- | --------------------------- |
| **chosen $H_0$** | correct                    | false negative<br>(Type II) |
| **chosen $H_1$** | false positive<br>(Type I) | correct                     |
## Possible errors in our example
In the case of data scientists coding as children, if we had a p-value less than or equal to the significance level, and rejected the null hypothesis, it's possible we made a false positive error. Although we thought data scientists started coding as children at a higher rate, it may not be true in the whole population. Conversely, if the p-value was greater than the significance level, and we failed to reject the null hypothesis, it's possible we made a false negative error.
## Let's practice!
Let's do some significant exercises.