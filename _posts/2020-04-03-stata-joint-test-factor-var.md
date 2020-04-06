----
title: "Linear Test with Dummies in Stata"
author: "Vinicius Lima"
tags: Stata
----
If we have many categories in a single variable and want to include them as controls in a regression, then it is easy to do that in Stata by using the `i.` operator. How can we test their joint significance after estimation?

```
. sysuse auto
(1978 Automobile Data)

. reg price mpg i.rep

      Source |       SS           df       MS      Number of obs   =        69
-------------+----------------------------------   F(5, 63)        =      4.39
       Model |   149020603         5  29804120.7   Prob > F        =    0.0017
    Residual |   427776355        63  6790100.88   R-squared       =    0.2584
-------------+----------------------------------   Adj R-squared   =    0.1995
       Total |   576796959        68  8482308.22   Root MSE        =    2605.8

------------------------------------------------------------------------------
       price |      Coef.   Std. Err.      t    P>|t|     [95% Conf. Interval]
-------------+----------------------------------------------------------------
         mpg |  -280.2615   61.57666    -4.55   0.000    -403.3126   -157.2103
             |
       rep78 |
          2  |   877.6347   2063.285     0.43   0.672     -3245.51     5000.78
          3  |   1425.657   1905.438     0.75   0.457    -2382.057    5233.371
          4  |   1693.841   1942.669     0.87   0.387    -2188.274    5575.956
          5  |   3131.982   2041.049     1.53   0.130    -946.7282    7210.693
             |
       _cons |   10449.99   2251.041     4.64   0.000     5951.646    14948.34
------------------------------------------------------------------------------

```

