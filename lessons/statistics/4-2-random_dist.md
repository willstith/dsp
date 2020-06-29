[Think Stats Chapter 4 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2005.html#toc41) (a random distribution)

Begin by importing necessary packages:

    import numpy as np
    import nsfg
    import first
    import thinkstats2
    import thinkplot

Generate 1000 random numbers and plot their PMF and CDF:

    t = np.random.random(1000)
    
    pmf = thinkstats2.Pmf(t)
    thinkplot.Pmf(pmf, linewidth=0.1)
    thinkplot.Config(xlabel='Random variate', ylabel='PMF')
    
    cdf = thinkstats2.Cdf(t)
    thinkplot.Cdf(cdf)
    thinkplot.Config(xlabel='Random variate', ylabel='CDF')
    
The PMF looks like a barcode of noise. The CDF shows a steady increase. The distribution is random.
