[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

# Solution

Import the necessary packages:

    import numpy as np
    import nsfg
    import first
    import thinkstats2
    import thinkplot

Compute the probability mass function (PMF) from respondents' data:

    resp = nsfg.ReadFemResp()
    pmf = thinkstats2.Pmf(resp.numkdhh, label='numkdhh')
    
Plot the true PMF of number of children and label the axes:

    thinkplot.Pmf(pmf)
    thinkplot.Config(xlabel='Number of children', ylabel='PMF')
    
Next, we define a function that will produce biased data as if we surveyed children directly:

    def BiasPmf(pmf, label):
        new_pmf = pmf.Copy(label=label)

        for x, p in pmf.Items():
            new_pmf.Mult(x, x)
        
        new_pmf.Normalize()
        return new_pmf
        
Using previous function to create biased data, plot that alongside the true data:

    biased = BiasPmf(pmf, label='biased')
    thinkplot.PrePlot(2)
    thinkplot.Pmfs([pmf, biased])
    thinkplot.Config(xlabel='Number of children', ylabel='PMF')
    
Compute the means of the biased and unbiased data:

    pmf.Mean()
      #Answer: 1.024205155043831
    biased.Mean()
      #Answer: 2.403679100664282
