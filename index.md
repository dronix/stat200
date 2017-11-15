@import "https://cdn.plot.ly/plotly-latest.min.js"

# STAT 200

A study guide for STAT 200, taught by professor Sagara, Yutaka, at the University of Maryland University College. The majority of the text is taken from [Introductory Statistics](http://openstaxcollege.org/files/textbook_version/hi_res_pdf/15/col11562-op.pdf) by OpenStax College, available under the [Creative Commons Attribution 3.0 Unported license](http://creativecommons.org/licenses/by/3.0/), professor Sagara's slides, and in-class materials. This is a work in progess...

**TODO-List**

- [ ] Sampling and Data
- [ ] Descriptive Statistics
- [ ] Probability Topics
- [ ] Descrete Random Variables
- [ ] Continuos Random Variables
- [ ] The Normal Distribution
- [ ] The Central Limit Theorem
- [ ] Confidence Intervals
- [ ] Hypothesis Testing With One Sample
- [ ] Hypothesis Testing With Two Samples
- [ ] The Chi-Square Distribution
- [ ] Linear Regression And Correlation
- [ ] F Distribution and One-Way ANOVA

#7. The Central Limit Theorem

According to the **central limit theorem**, the distribution of sample means and the sums tend to follow a normal distribution. If we were to collect samples of size *n* that are "large enough," calculate the sum of each sample and create a historgram, then the resulting histogram will again tend to have a normal-bell-shape.

````python {cmd=true matplotlib=true}
import numpy as np
import matplotlib.mlab as mlab
import matplotlib.pyplot as plt

np.random.seed(19680801)

# example data
mu = 100  # mean of distribution
sigma = 15  # standard deviation of distribution
x = mu + sigma * np.random.randn(437)

num_bins = 50

fig, ax = plt.subplots()

# the histogram of the data
n, bins, patches = ax.hist(x, num_bins, normed=1)

# add a 'best fit' line
y = mlab.normpdf(bins, mu, sigma)
ax.plot(bins, y, '--')
ax.set_xlabel('Smarts')
ax.set_ylabel('Probability density')
ax.set_title(r'Histogram of IQ: $\mu=100$, $\sigma=15$')

# Tweak spacing to prevent clipping of ylabel
fig.tight_layout()
plt.show()
````

##7.1 Finding the mean and standard deviation of a sample mean

The **mean** of a **sample mean** is represented as $\mu_X$
The **standard deviation** is represnted as $\sigma_X$ and can be calculated by using the following formula: $$\frac {\mu_X}{\sqrt n}$$

###Example 7.1

In a recent study reported Oct. 29, 2012 on the Flurry Blog, the ==mean== age of tablet users is ==34 years==. Suppose the ==standard deviation== is ==15 years==. Take a sample of size ==$n$ = 100==. 

- a. What are the mean and standard deviation for the sample mean ages of tablet users?
- b. Find the probability that the sample mean age is more than 30 years.
- c. Find the 95^th^ percentile for the sample mean age. 

#### Solution

Before finding the solution we must identify the information given.

- $\mu = 34$
- $n = 100$
- $\sigma = 15$

**a.)** Since $\mu_X$ is representative of $\mu$, we can say that ==$\mu_X = 34$==, or that the mean of the sample is 34. To find the standard deviation, we use the formula
$$\sigma_X = \frac {\sigma}{\sqrt n}$$
Then we plug in the values that we were given
$$\sigma_X = \frac {15}{\sqrt {100}} = 1.5$$
Therefore, we can say that ==$\sigma_X = 1.5$==, or that the standard deviation for the sample is 1.5.

**b.)** The second questions is asking for the **probability** that the sample mean age is more than ==30 years==. We can find this information by determening the **z-score** and then looking for the **area** or percentage to the **RIGHT** of **z**.

So we begin by finding the **z-score** using the information provided and the result of $\sigma_x$ from the previous question:
$$\begin{gathered} z = \frac {\bar{x} - \mu}{\frac{\sigma}{\sqrt{n}}} \\ \\ z = \frac {30 - 34}{1.5} \\ \\ z = -2.67 \\ z = 0.0038\end{gathered}$$

As you can see the area to the **LEFT** of the **z** value is 0.0038, this means that there is a 0.38% probability that the sample mean age is 30 years or **less**. However, the problem is asking for 30 years or **more**.

Therefore, we must subtract 0.38% from 100%.
$$100\% - 0.08\% = 99.62\%$$

Our result for the probability that the sample mean age is more than 30 years, is ==99.62%==.


**c.)** In this scenerio, we are told to find the 95^th^ percentile of the sample mean, meaning we need to find the sample mean that has a probability of **95% or less**. 

We start by using the **z-score** formula. $$z = \frac {\bar{x} - \mu}{\frac{\sigma}{\sqrt{n}}}$$

In this case we are looking for the value of $\bar{x}$. We can use the **z-score** formula to solve for $\bar{x}$.
$$\bar{x} = (z)(\frac{\sigma}{\sqrt{n}}) + \mu$$

We can then use the **z-score** table to find the value of **z** given the probability of 95% or 0.95.

| Z | 0.00 | 0.01 | 0.02 | 0.03 | ==0.04== | ==0.05== | 0.06 | 0.07 | 0.08 | 0.09 |
| -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- |
| 1.40 | 0.9192 | 0.9207 | 0.9222 | 0.9236 | 0.9251 | 0.9265 | 0.9279 | 0.9292 | 0.9306 | 0.9319 |
| 1.50 | 0.9332 | 0.9345 | 0.9357 | 0.9370 | 0.9382 | 0.9394 | 0.9406 | 0.9418 | 0.9429 | 0.9441 |
| ==1.60== | 0.9452 | 0.9463 | 0.9474 | 0.9484 | ==0.9495== | ==0.9505== | 0.9515 | 0.9525 | 0.9535 | 0.9545 |

As you can see, in our table, 0.95 falls between 1.64 and 1.65, so we can estimate **z** to be ==1.645==.

Now we go back to our formula using our **z** value and solve for $\bar{x}$.

$$\begin{gathered} \bar{x} = (z)(\frac{\sigma}{\sqrt{n}}) + \mu \\ \\ \bar{x} = (1.645)(1.5) + 34 \\ \\ \bar{x} = 36.4675 \\ \\ \bar{x} \approx 36.5\end{gathered}$$

Our result for the 95^th^ percentile for the sample mean age, is ==36.5==.


#8. Confidence Intervals

**Confidence Interval (CI)** gives the range with various certainty (90%, 95%, 99%, etc.).

**Margin of error (EBM)** depends on the confidence level, sample size, and known or estimated deviation

##8.1 Definitions

- $\mu$ = population mean
- $\sigma$ = population standard deviation
- $\bar{x}$ = sample mean
- $n$ = number of sample values
- $E$ = margin of error
- $z$ = z-score
- $\alpha$ = area split equally between the two tails 
- $z_{\alpha/2}$ = z-score separating an area $\alpha/2$ in the right tail of the standard normal distribution
- $t$ = student $t$ distribution
- $t_{\alpha/2}$ = t-score separating an area $\alpha/2$ in the right tail of the standard normal distribution

##8.2 $Z$-score vs $T$-score

### Similarities
 - Both z-score and t-socore require ==$n > 30$==, meaning the sample size needs to be greater than 30.
 - Both require the population to be ==normally distributed==.

### Differences

- Use the ==$z$-score== if ==$\sigma$ is known==.
- Use the ==$t$-score== if ==$\sigma$ is **NOT** known==.

If none of those criterias are met, then use **nonparametric** or **bootstrapping methods**.

### Example 8.1

A study of ==415 kindergarten students== showed that they have seen on average ==5,000 hours== of TV. If the ==sample standard deviation== of the population is ==900==, find the ==95% confidence level== of the ==mean== for all students. If a parent claimed that his children watched ==4,000 hours==, would the claim be believable.

#### Solution

Lets identify the information given.

- $n$ = 415
- $\bar{x}$ = 5,000
- $\sigma_x$ = 900
- $CL$ = 95% or 0.95
- $x$ = 4,000

And the questions being asked are

- a. What is the 95% confidence level of the mean of all students?
- b. If a parent claimed that his children watched 4,000 hours, would the claim be believable.

First we must determine whether to use the **z-score** or the **t-score** distribution. The problem provides us with ==$\sigma_x$ = 900==. Therefore, we should use the **z-score** distribution. 

Then we look at the first question in the problem which asks us to find the ==95% confidence level== of the ==mean== of all students. In other words, we are being told that $CL$ = 95% or ==0.95==, and we need to find the **confidence interval** estimate of that percentage. Remember that $CL$, or the **confidence level**, is the **area** in the middle of the standard normal distribution, and that the **confidence interval** is not just one number, it is **a set of numbers**.

We can take a look at the graph below to understand it better.


![ch08_CL_graph](/assets/ch08_CL_graph_8qjx9u6z2.png)


The confidence interval can be expressed in defferent ways $$\begin{gathered} \bar{x} - E < \mu < \bar{x} + E \\ or \\ \bar{x} \pm E \\ or \\ (\bar{x} - E, \bar{x} + E) \end{gathered}$$

So if we update the graph we have

![ch08_CL_graph_extended](/assets/ch08_CL_graph_extended_h7ngy75tm.png)

In order to find the confidence interval, or ==$\bar{x} - E < \mu < \bar{x} + E$==, we need to first find the value of $E$, which is the **margin of error**.
$$E = z_{\alpha/2} \cdot \frac{\sigma}{\sqrt{n}}$$

As you know, $\sigma_x = \frac{\sigma}{\sqrt{n}}$

If we plug in the values that we were given, we're left with the following
$$E = z_{\alpha/2} \cdot \frac{900}{\sqrt{415}}$$

We need to find $z_{a/2}$ in order to solve the equation above. 

Since $CL = 1 - \alpha$ , we can infer that ==$\alpha = 1 - CL$==.

$$\begin{gathered} \alpha = 1 - CL \\ \alpha = 1 - 0.95 \\ \alpha = 0.05\end{gathered}$$

Since $\alpha = 0.05$, we can say that $z_{0.05/2} = z_{0.025}$. This means that the area to the **RIGHT** of $z_{0.025}$ is 0.025, and the area to the **LEFT** of $z_{0.025}$ is $1 - 0.025 = 0.975$. In our scenario, we are concerned with the area to the **LEFT** of $z_{0.025}$, wich is ==0.975==.

We can then use the **z-score** table to look up the $z$ value given an area of 0.975.

| Z | 0.00 | 0.01 | 0.02 | 0.03 | 0.04 | 0.05 | ==0.06== | 0.07 | 0.08 | 0.09 |
| -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- |
| 1.70 | 0.9554 | 0.9564 | 0.9573 | 0.9582 | 0.9591 | 0.9599 | 0.9608 | 0.9616 | 0.9625 | 0.9633 |
| 1.80 | 0.9641 | 0.9649 | 0.9656 | 0.9664 | 0.9671 | 0.9678 | 0.9686 | 0.9693 | 0.9699 | 0.9706 |
| ==1.90== | 0.9713 | 0.9719 | 0.9726 | 0.9732 | 0.9738 | 0.9744 | ==0.9750== | 0.9756 | 0.9761 | 0.9767 |
| 2.00 | 0.9772 | 0.9778 | 0.9783 | 0.9788 | 0.9793 | 0.9798 | 0.9803 | 0.9808 | 0.9812 | 0.9817 |

Looking at the table we can then say that given that the area to the left of $z$ is 0.975, the **z-score** is ==1.96==.

We can then go back to our confidence interval formula and plugin the remaining value
$$\begin{gathered} E = z_{\alpha/2} \cdot \frac{900}{\sqrt{415}} \\ \\ E = 1.96 \cdot \frac{900}{\sqrt{415}} \\ \\E = 86.60\end{gathered}$$

This result ==$E = 86.60$== means that the margin of error is 86.60.

Now we have all the information neccessary to answer $\bar{x} - E < \mu < \bar{x} + E$. Lets plug in the values.
$$\begin{gathered} \bar{x} - E < \mu < \bar{x} + E \\ 5,000 - E < \mu < 5,000 + E \\ 5,000 - 86.60 < \mu < 5,000 + 86.60 \\ 4,913.4 < \mu < 5,086.6 \\ 4,913 < \mu < 5,087 \end{gathered}$$

**a.)** So the answer the first question is ==$4,913.4 < \mu < 5,086.6$==.

With this information we can then answer the second question. 

**b.)** If a parent claimed that his children watched 4,000 hours, it would not be believable since it is outside of the confidence interval, 4,000 < 4,913.

### Example 8.2

A health care professional wishes to estimate the birth weights of infants. ==How large a sample== must be obtained if she desires to be ==90% confident== that the true mean is ==within 2 ounces== of the sample mean? Assume ==$\sigma = 8$ ounces==.

#### Solution

Lets list all the given information.

- $n$ = ?
- $CL$ = 90% or 0.90
- $E$ = 2
- $\sigma$ = 8

The problem is asking for "how large a sample must be", meaning the value of $n$.

Lets begin be determining if we can use the **z-score** or the **t-distribution**. We are given $\sigma = 8$. Therefore we can use the **z-score** distribution.

In order to find $n$ with the information that we have, we can use:
$$E = z_{a/2} \cdot \frac{\sigma}{\sqrt{n}}$$

Using that formula we can solve for $n$ and we're left with:
$$n = [({z_{\alpha/2 \cdot \sigma})/E}]^2$$ 

As the previous example, we need to find the value of $z_{\alpha/2}$, more specifically the **area** to the **LEFT** of $z_{\alpha/2}$.

We know that $\alpha = 1 - CL$, and since we were given $CL$ = 0.90, we can say that $\alpha = 1 - 0.90$ or $0.10$.

Therefore, $z_{\alpha/2} = 0.05$, and the area to the **LEFT** of $z_{0.05}$ is $1 - 0.05 =$ ==$0.95$==.

So if we search for the value of $z$ in the **z-score** table for the area of 0.95...

| Z | 0.00 | 0.01 | 0.02 | 0.03 | ==0.04== | ==0.05== | 0.06 | 0.07 | 0.08 | 0.09 |
| -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- |
| 1.40 | 0.9192 | 0.9207 | 0.9222 | 0.9236 | 0.9251 | 0.9265 | 0.9279 | 0.9292 | 0.9306 | 0.9319 |
| 1.50 | 0.9332 | 0.9345 | 0.9357 | 0.9370 | 0.9382 | 0.9394 | 0.9406 | 0.9418 | 0.9429 | 0.9441 |
| ==1.60== | 0.9452 | 0.9463 | 0.9474 | 0.9484 | ==0.9495== | ==0.9505== | 0.9515 | 0.9525 | 0.9535 | 0.9545 |

...we don't have 0.95 exactly in this table, but we can estimate that it is between 1.64 and 1.65, so we can go with ==1.645==.

Now we can go back to our formula to find the value of $n$.
$$\begin{gathered} n = [({z_{\alpha/2 \cdot \sigma})/E}]^2 \\ n =[(1.645 \cdot 8)/2]^2 \\ n = [(13.16)/2]^2 \\ n = 6.8^2 \\ n = 43.2964 \\ n \approx 44 \end{gathered}$$

Notice that ==$n = 43.2964$==, but we must always round UP to the next higher integer to ensure that the sample size is large enough.

Therefore, our final answer is ==$n = 44$==.




# Testing Graphs

##1. First Graph
````javascript {cmd=true element="<div id='tester'></div>"}
var TESTER = document.getElementById('tester')
Plotly.plot(TESTER, [{
    x: [1, 2, 3, 4],
    y: [1, 2, 3, 4]
}, {
    margin: {f: 0}
}])
''
````

##2. Second Graph

````javascript {cmd=true element="<div id='myDiv'></div>}
var y0=[],y1=[]
for (var i = 0; i < 50; i ++) 
{
    y0[i] = Math.random();
    y1[i] = Math.random();
}

var trace1 = {
  y: y0,
  type: 'box'
};

var trace2 = {
  y: y1,
  type: 'box'
};

var data = [trace1, trace2];

Plotly.newPlot('myDiv', data);

````

##3. Third Graph

````javascript {cmd=true element="<div id='myDiv2'></div>}
var trace1 = {
  x: [1, 2, 3, 4, 4, 4, 8, 9, 10],
  type: 'box',
  name: 'Set 1'
};
var trace2 = {
  x: [2, 3, 3, 3, 3, 5, 6, 6, 7],
  type: 'box',
  name: 'Set 2'
};

var data = [trace1, trace2];

var layout = {
  title: 'Horizontal Box Plot'
};

Plotly.newPlot('myDiv2', data, layout);

````

##4. Fourth Graph

````python {cmd=true matplotlib=true}
import matplotlib.pyplot as plt
plt.plot([1,2,3, 4])
plt.show()
````


###5. Fifth Graph

````python {cmd=true matplotlib=true}
import numpy as np
import matplotlib.pyplot as plt


x1 = np.linspace(0.0, 5.0)
x2 = np.linspace(0.0, 2.0)

y1 = np.cos(2 * np.pi * x1) * np.exp(-x1)
y2 = np.cos(2 * np.pi * x2)

plt.subplot(2, 1, 1)
plt.plot(x1, y1, 'o-')
plt.title('A tale of 2 subplots')
plt.ylabel('Damped oscillation')

plt.subplot(2, 1, 2)
plt.plot(x2, y2, '.-')
plt.xlabel('time (s)')
plt.ylabel('Undamped')

plt.show()
````



