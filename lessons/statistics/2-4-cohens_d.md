[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

# Solution

  Begin by importing packages
  
    import numpy as np
    import nsfg
    import first

  Define first-borns and others as variables
  
    preg = nsfg.ReadFemPreg()
    live = preg[preg.outcome == 1]
    firsts = live[live.birthord == 1]
    others = live[live.birthord != 1]

  Compute mean total weight of each group
  
    firsts.totalwgt_lb.mean(), others.totalwgt_lb.mean()
        #Answer: (7.201094430437772, 7.325855614973262) first babies are lighter

  Define function to take in 2 groups and return their Cohen Effect Size
 
     def CohenEffectSize(group1, group2):
    
        diff = group1.mean() - group2.mean()

        var1 = group1.var()
        var2 = group2.var()
        n1, n2 = len(group1), len(group2)

        pooled_var = (n1 * var1 + n2 * var2) / (n1 + n2)
        d = diff / np.sqrt(pooled_var)
        return d

  Call previous function to compare difference in birthweight and preg length
  
    CohenEffectSize(firsts.totalwgt_lb, others.totalwgt_lb)
        #Answer: -0.088672927072602
    CohenEffectSize(firsts.prglngth, others.prglngth)
        #Answer: 0.028879044654449883
    
The Cohen Effect Size of birthweight between first-born babies and others
is greater than that for pregnancy length.
