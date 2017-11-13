
@import "https://cdn.plot.ly/plotly-latest.min.js"

# STAT 200

A study guide for STAT 200, taught by professor Sagara, Yutaka, at the University of Maryland University College. The majority of the text is taken from [Introductory Statistics](http://openstaxcollege.org/files/textbook_version/hi_res_pdf/15/col11562-op.pdf) by OpenStax College, available under the [Creative Commons Attribution 3.0 Unported license](http://creativecommons.org/licenses/by/3.0/). This is a work in progess...

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

$f(x) = sin(x) + 2$

$$\sum_{n=1}$$

#7. The Central Limit Theorem

According to the **central limit theorem**, the distribution of sample means and the sums tend to follow a normal distribution. If we were to collect samples of of size *n* that are "large enough," calculate the sum of each sample and create a historgram, then the resulting histogram will again tend to have a normal-bell-shape.

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
- b. Find the probability that the sample mean age is morethan 30 years.
- c. Find the 95^th^ percentile for the sample mean age. 

#### Solution

Before finding the solution we must identify the information given.

- $\mu = 34$
- $n = 100$
- $\sigma = 15$

**a.)** Since $\mu_X$ is the same as $\mu$, we can say that ==$\mu = 34$==, or that the mean of the sample is 34. To find the standard deviation, we use the formula
$$\sigma_X = \frac {\sigma}{\sqrt n}$$
Then we plug in the values that we were given
$$\sigma_X = \frac {15}{\sqrt {100}} = 1.5$$
Therefore, we can say that ==$\sigma_X = 1.5$==, or that the standard deviation for the sample is 1.5.

**b.)**



```python {cmd=true matplotlib=true}
import matplotlib.pyplot as plt
plt.plot([1,2,3, 4])
plt.show()
```

##1.2 Second Graph

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

#2. Third Graph

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

#3. Fourth Graph

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

#4. Fifth Graph

````python {cmd=true matplotlib=true}
import matplotlib.pyplot as plt
plt.plot([1,2,3, 4])
plt.show()
````

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



