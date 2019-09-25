
# The Normal Distribution - Lab

## Introduction
In this lab, you'll learn how to generate random normal distributions in Python. You'll learn how to visualize a histogram and build a density function using the formula. 
## Objectives
You will be able to:
* Generate random normal distributions in Python with given parameters
* Calculate the density function for normal distributions
* Use seaborn to visualize distributions with histograms and density functions

## A quick refresher! 

Here's the formula for the normal distribution density function once more:

$$ \large N(x) = \dfrac{1}{\sigma \sqrt {2\pi }}e^{-\dfrac{(x-\mu)^2}{2\sigma^2}}$$

Here, 
- $\mu$ is the mean
- $\sigma$ is the standard deviation
- $\pi \approx 3.14159 $ 
- $ e \approx 2.71828 $


## First generate a normal distribution containing 5000 values with $\mu=14$ and $\sigma = 2.8$


```python
# Generate a random normal variable with given parameters , n=5000
import numpy as np

mu, sigma = 14, 2.8
n = 5000
s = np.random.normal(mu, sigma, n)
```

## Calculate a normalized histogram for this distribution in matplotlib, with bin size = 20

Make sure to get the bin positions and counts for each of the obtained bins. You can use [official documentation](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.hist.html) to view input and output options for `plt.hist()`


```python
import matplotlib.pyplot as plt
# Create the bins and histogram
count, bins, ignored = plt.hist(s, 20, density=True)
```


![png](index_files/index_6_0.png)


## Use the formula to calculate the density function with $\mu$, $\sigma$ and bin information obtained before


```python
# Calculate the normal Density function 
density = 1/(sigma * np.sqrt(2 * np.pi)) * np.exp( - (bins - mu)**2 / (2 * sigma**2))
```

## Plot the histogram and density function


```python
# Plot histogram along with the density function
plt.hist(s, 20, normed=True)
plt.plot(bins, density)
plt.show()
```


![png](index_files/index_10_0.png)


## Visualize the distribution using seaborn and plot the KDE


```python
import seaborn as sns
sns.distplot(s, bins=20, kde=True)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x1a121adac8>




![png](index_files/index_12_1.png)


## Summary

In this lab, you learned how to generate random normal distributions in Python using Numpy. You also calculated the density for normal distributions using the general formula as well as seaborn's KDE. Next, you'll move on to learn how normal distributions are used to answer analytical questions.
