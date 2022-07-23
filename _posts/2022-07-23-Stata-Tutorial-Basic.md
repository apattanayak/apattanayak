[<img alt="Back to Blog Home" width="80px" src="/images/back2.png" align="left"/>](https://apattanayak.github.io/Blog.html)
[<img alt="Back to Blog Home" width="80px" src="/images/back2.png" align="right"/>](https://apattanayak.github.io/Blog.html)
<p style="clear: both;">


This tutorial will show the basic use of Stata and python together.




```python
%stata sysuse auto
```

    (1978 automobile data)
    


```python
%stata describe, detail
```

    
    Contains data from C:\Program Files\Stata17/ado\base/a/auto.dta
     Observations:            74                  1978 automobile data
        Variables:            12                  13 Apr 2020 17:45
            Width:            43                  
                                                  (_dta has notes)
    -------------------------------------------------------------------------------
    Variable      Storage   Display    Value
        name         type    format    label      Variable label
    -------------------------------------------------------------------------------
    make            str18   %-18s                 Make and model
    price           int     %8.0gc                Price
    mpg             int     %8.0g                 Mileage (mpg)
    rep78           int     %8.0g                 Repair record 1978
    headroom        float   %6.1f                 Headroom (in.)
    trunk           int     %8.0g                 Trunk space (cu. ft.)
    weight          int     %8.0gc                Weight (lbs.)
    length          int     %8.0g                 Length (in.)
    turn            int     %8.0g                 Turn circle (ft.)
    displacement    int     %8.0g                 Displacement (cu. in.)
    gear_ratio      float   %6.2f                 Gear ratio
    foreign         byte    %8.0g      origin     Car origin
    -------------------------------------------------------------------------------
    Sorted by: foreign
    


```python
%stata summarize
```

    -------------+---------------------------------------------------------
            make |          0
           price |         74    6165.257    2949.496       3291      15906
             mpg |         74     21.2973    5.785503         12         41
           rep78 |         69    3.405797    .9899323          1          5
    
        Variable |        Obs        Mean    Std. dev.       Min        Max
        headroom |         74    2.993243    .8459948        1.5          5
    -------------+---------------------------------------------------------
           trunk |         74    13.75676    4.277404          5         23
          weight |         74    3019.459    777.1936       1760       4840
          length |         74    187.9324    22.26634        142        233
            turn |         74    39.64865    4.399354         31         51
    displacement |         74    197.2973    91.83722         79        425
    -------------+---------------------------------------------------------
      gear_ratio |         74    3.014865    .4562871       2.19       3.89
         foreign |         74    .2972973    .4601885          0          1
    


```python
%%stata
grstyle init
grstyle set graphsize 5 5
grstyle set imesh, horizontal compact
grstyle set linewidth 0.5pt: axisline xyline
grstyle set color matplotlib, select(12) saturate(25) op(50): p#markfill
grstyle set color matplotlib, select(12) saturate(25) op(0): p#markline
grstyle set ci lime, saturate(25) op(25)
gr tw (scatter price mpg) (lpolyci price mpg), legend(off)
addplot: histogram
```

    
    . grstyle init
    
    . grstyle set graphsize 5 5
    
    . grstyle set imesh, horizontal compact
    
    . grstyle set linewidth 0.5pt: axisline xyline
    
    . grstyle set color matplotlib, select(12) saturate(25) op(50): p#markfill
    
    . grstyle set color matplotlib, select(12) saturate(25) op(0): p#markline
    
    . grstyle set ci lime, saturate(25) op(25)
    
    . gr tw (scatter price mpg) (lpolyci price mpg), legend(off)
    
    . 
    


    
![svg](/images/output_5_1.svg)
    

