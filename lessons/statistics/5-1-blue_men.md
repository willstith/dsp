[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

Solution

Import necessary packages:

    import numpy as np
    import nsfg
    import first
    import analytic

    import thinkstats2
    import thinkplot
    
    import scipy.stats
    
Assign parameters to variables and create normal distribution from them using scipy.stats:

    mu = 178
    sigma = 7.7
    dist = scipy.stats.norm(loc=mu, scale=sigma)
    
Compute cdfs of 5'10" and 6'1" (converted to cm), then the difference between them to get answer:

    low = dist.cdf(177.8)    # 5'10" in cm
    high = dist.cdf(185.4)   # 6'1" in cm
    between = high - low
    between

Answer: 34.20946829459531%
