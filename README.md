# ASN5.1. Paper Replication: Understanding the Data
2024 FIRE198 Sustainability Analytics

## Part 1. Understanding the Data

### Step 1

Let RStudio know that you plan to use the tidyverse package with the
script below. You just need to run it.

``` r
library("tidyverse")
```

    ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ✔ dplyr     1.1.1     ✔ readr     2.1.4
    ✔ forcats   1.0.0     ✔ stringr   1.5.0
    ✔ ggplot2   3.5.0     ✔ tibble    3.2.1
    ✔ lubridate 1.9.3     ✔ tidyr     1.3.0
    ✔ purrr     1.0.1     
    ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ✖ dplyr::filter() masks stats::filter()
    ✖ dplyr::lag()    masks stats::lag()
    ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

### Step 2

Notice that the folder **EPA AMPD** appeared after you have cloned the
repository. Within the folder are 5 files that shows monthly emissions
from each electricity generating unit each year.

The read.csv() function allows you to upload files into the RStudio
environment. The script below upload emissions data in the year 2007
from the folder EPA AMPD and store it as **df2007**. You just need to
run it.

``` r
df2007<-read.csv("EPA AMPD/emission_2007.csv")
```

### Step 3

Use the **names** function to preview the variable names. This can be
done by using the script below.

``` r
names(df2007)
```

     [1] "X"                        "State"                   
     [3] "Facility.Name"            "Facility.ID..ORISPL."    
     [5] "Unit.ID"                  "Associated.Stacks"       
     [7] "Month"                    "Year"                    
     [9] "Program.s."               "Operating.Time"          
    [11] "Gross.Load..MW.h."        "Steam.Load..1000lb."     
    [13] "SO2..tons."               "Avg..NOx.Rate..lb.MMBtu."
    [15] "NOx..tons."               "CO2..short.tons."        
    [17] "Heat.Input..MMBtu."       "EPA.Region"              
    [19] "NERC.Region"              "County"                  

#### Question 1: What three variables indicate the total amount of greenhouse gases and pollutants that were being emitted? (3 points)

#### Answer: SO2..tons. , NOx..tons. , CO2..short.tons.

#### Question 2: What variables are used to identify each electricity-generating unit? (2 points)

#### Answer: Facility.ID..ORISPL., Unit.ID

#### Question 3: What two variables identify the time the gases were emitted? (2 points)

#### Answer: Month, Year

### Step 4

Use the **table** function to preview the values in each column. The
script below shows how many values are there in the column **State.**
You just have to run it.

``` r
table(df2007$State)
```


      AL   AR   AZ   CA   CO   CT   DC   DE   FL   GA   IA   ID   IL   IN   KS   KY 
    1308  555  912 2307  726  588   60  420 2379 1560  606   72 3114 1968  576 1200 
      LA   MA   MD   ME   MI   MN   MO   MS   MT   NC   ND   NE   NH   NJ   NM   NV 
    1152  894  528  156 1692  618 1050 1068   96 1698  144  384  120 1551  408  492 
      NY   OH   OK   OR   PA   RI   SC   SD   TN   TX   UT   VA   VT   WA   WI   WV 
    3738 2022  828  177 2256  132  972   96 1002 3867  330 1380   12  195 1032  846 
      WY 
     228 

#### Question 4: Which state has the highest number of electricity-generating units? (1 point)

#### Answer: TX

### Step 5

Use the **summary** function to summarize the **df2007** dataframe. The
code is shown below. You just have to run it.

``` r
summary(df2007)
```

           X            State           Facility.Name      Facility.ID..ORISPL.
     Min.   :    1   Length:49515       Length:49515       Min.   :     3      
     1st Qu.:12380   Class :character   Class :character   1st Qu.:  2384      
     Median :24758   Mode  :character   Mode  :character   Median :  6166      
     Mean   :24758                                         Mean   : 31499      
     3rd Qu.:37137                                         3rd Qu.: 55101      
     Max.   :49515                                         Max.   :880094      
                                                                               
       Unit.ID          Associated.Stacks      Month             Year     
     Length:49515       Length:49515       Min.   : 1.000   Min.   :2007  
     Class :character   Class :character   1st Qu.: 4.000   1st Qu.:2007  
     Mode  :character   Mode  :character   Median : 7.000   Median :2007  
                                           Mean   : 6.522   Mean   :2007  
                                           3rd Qu.: 9.000   3rd Qu.:2007  
                                           Max.   :12.000   Max.   :2007  
                                                                          
      Program.s.        Operating.Time  Gross.Load..MW.h. Steam.Load..1000lb.
     Length:49515       Min.   :  0.0   Min.   :      0   Min.   :       0   
     Class :character   1st Qu.:  8.7   1st Qu.:   1900   1st Qu.:   48918   
     Mode  :character   Median :169.4   Median :  25403   Median :  122028   
                        Mean   :305.3   Mean   :  78076   Mean   :  206064   
                        3rd Qu.:663.8   3rd Qu.:  97616   3rd Qu.:  249622   
                        Max.   :744.0   Max.   :1033073   Max.   :15005348   
                                        NA's   :12853     NA's   :45498      
       SO2..tons.       Avg..NOx.Rate..lb.MMBtu.   NOx..tons.     
     Min.   :   0.000   Min.   :0.000            Min.   :   0.00  
     1st Qu.:   0.012   1st Qu.:0.040            1st Qu.:   0.85  
     Median :   0.190   Median :0.108            Median :   5.19  
     Mean   : 248.969   Mean   :0.196            Mean   :  82.71  
     3rd Qu.: 182.773   3rd Qu.:0.300            3rd Qu.:  66.10  
     Max.   :9847.540   Max.   :3.600            Max.   :3839.40  
     NA's   :13631      NA's   :9031             NA's   :8854     
     CO2..short.tons.  Heat.Input..MMBtu.   EPA.Region     NERC.Region       
     Min.   :      0   Min.   :       0   Min.   : 1.000   Length:49515      
     1st Qu.:   1668   1st Qu.:   24956   1st Qu.: 3.000   Class :character  
     Median :  21110   Median :  239149   Median : 5.000   Mode  :character  
     Mean   :  71492   Mean   :  709371   Mean   : 4.764                     
     3rd Qu.:  71145   3rd Qu.:  875079   3rd Qu.: 6.000                     
     Max.   :1283545   Max.   :12510060   Max.   :10.000                     
     NA's   :13633     NA's   :9025                                          
        County         
     Length:49515      
     Class :character  
     Mode  :character  
                       
                       
                       
                       

#### Question 5: What is the average gross load? (1 point)

#### Answer: 78,076 tons MwH

#### Question 6: How many missing values (or NAs) are in the column NOx..tons.? (1 point)

#### Answer: 8,854

### Step 6

Let’s investigate the missing data in **NOx..tons.** The script below
uses the **filter** function and creates a new dataframe called **df0**
that contains only observations with NA values in **NOx..tons.** You
just have to run it.

``` r
df0<-df2007 %>%
  filter(is.na(NOx..tons.))
```

#### Question 7: What is the average gross load in df0? (1 point for the correct code and 1 point for the correct answer)

#### Hint: Use the summary function.

``` r
summary(df0)
```

           X            State           Facility.Name      Facility.ID..ORISPL.
     Min.   :    2   Length:8854        Length:8854        Min.   :     3      
     1st Qu.:12635   Class :character   Class :character   1st Qu.:  1912      
     Median :23100   Mode  :character   Mode  :character   Median :  4195      
     Mean   :23469                                         Mean   : 35083      
     3rd Qu.:34185                                         3rd Qu.: 55128      
     Max.   :49490                                         Max.   :880094      
                                                                               
       Unit.ID          Associated.Stacks      Month             Year     
     Length:8854        Length:8854        Min.   : 1.000   Min.   :2007  
     Class :character   Class :character   1st Qu.: 3.000   1st Qu.:2007  
     Mode  :character   Mode  :character   Median : 5.000   Median :2007  
                                           Mean   : 6.089   Mean   :2007  
                                           3rd Qu.: 9.000   3rd Qu.:2007  
                                           Max.   :12.000   Max.   :2007  
                                                                          
      Program.s.        Operating.Time     Gross.Load..MW.h. Steam.Load..1000lb.
     Length:8854        Min.   : 0.00000   Min.   :   0.0    Min.   : 1         
     Class :character   1st Qu.: 0.00000   1st Qu.:   0.0    1st Qu.:15         
     Mode  :character   Median : 0.00000   Median :   0.0    Median :29         
                        Mean   : 0.01807   Mean   : 306.3    Mean   :29         
                        3rd Qu.: 0.00000   3rd Qu.:   0.0    3rd Qu.:43         
                        Max.   :55.50000   Max.   :3674.0    Max.   :57         
                                           NA's   :8834      NA's   :8852       
       SO2..tons.    Avg..NOx.Rate..lb.MMBtu.   NOx..tons.   CO2..short.tons.  
     Min.   :0.000   Min.   :0.000            Min.   : NA    Min.   :   0.000  
     1st Qu.:0.000   1st Qu.:0.000            1st Qu.: NA    1st Qu.:   0.007  
     Median :0.000   Median :0.000            Median : NA    Median :   0.200  
     Mean   :0.176   Mean   :0.180            Mean   :NaN    Mean   : 318.832  
     3rd Qu.:0.000   3rd Qu.:0.013            3rd Qu.: NA    3rd Qu.:   7.022  
     Max.   :2.164   Max.   :2.379            Max.   : NA    Max.   :2805.603  
     NA's   :8837    NA's   :8834             NA's   :8854   NA's   :8839      
     Heat.Input..MMBtu.   EPA.Region     NERC.Region           County         
     Min.   :    0.00   Min.   : 1.000   Length:8854        Length:8854       
     1st Qu.:    0.00   1st Qu.: 4.000   Class :character   Class :character  
     Median :    0.82   Median : 5.000   Mode  :character   Mode  :character  
     Mean   : 3309.04   Mean   : 4.731                                        
     3rd Qu.:   37.46   3rd Qu.: 6.000                                        
     Max.   :46584.93   Max.   :10.000                                        
     NA's   :8830                                                             

#### Answer: 306 MwH

### Step 8

Because the average gross load for observations with NA values in
**NOx..tons.** are much lower than the average, we will replace NA
values in the column **NOx..tons.** with 0. To do that, you must combine
the **mutate** and **ifelse** functions.

The script below allows you to create a new column named **NOx_emit** in
**df2**.

If **NOx..tons.** equals NA, then **NOx_emit** will be zero.

Otherwise, **NOx_emit** is equal to **NOx..tons.**

The code is shown below. You just have to run it.

``` r
df2<-df2007 %>% 
  mutate(NOx_emit=ifelse(is.na(NOx..tons.),0,NOx..tons.))
```

## Part 2: Preparing Data for Analysis

You will use the **filter** and **mutate** functions to identify which
facilities were regulated by the NOx Budget Program. Combined with the
codes you will write in next week’s assignment, you will be able to
create the figure below, which compares NOx emissions before and after
the implementation of the NOx Budget Program.

<img src="Figure%201%20Rep.png" data-fig-align="center" width="500" />

### Step 1: Upload data (2 points)

In Part 1, Step 2, you have uploaded emissions data from 2007. You need
to do the same thing for 2001, 2002, 2005, and 2006.

``` r
df2001<-read.csv("EPA AMPD/emission_2001.csv")
df2002<-read.csv("EPA AMPD/emission_2002.csv")
df2005<-read.csv("EPA AMPD/emission_2005.csv")
df2006<-read.csv("EPA AMPD/emission_2006.csv")
```

### Step 2: Combine data

Use the **rbind** function to stack all emissions data in 2001, 2002,
2005, 2006, and 2007 together into one data frame, **df**. The code is
shown below. You just have to run it.

``` r
df<-rbind(df2001, df2002, df2005, df2006, df2007)
```

### Step 3: Replace missing values with 0 (1 point)

Repeat what you did in Part 1, Step 8 to create a new dataframe named
**df2** with a new column named **NOx_emit**.

**NOx_emit** will to 0 if **NOx..tons.** is equal to NA. Otherwise,
**NOx_emit** will equal to **NOx..tons.**

``` r
df2<-df %>% 
  mutate(NOx_emit=ifelse(is.na(NOx..tons.),0,NOx..tons.))
```

#### Question 8: What are the six possible values for the Program.s. variable? (1 point for the correct code and 1 point for the correct answer)

``` r
table(df2$Program.s.)
```


           ARP   ARP, NBP ARP, NHNOX   ARP, OTC        NBP        OTC 
        122193      57849        360       8841      23379      11208 

#### Answer:

ARP

ARP, NBP

ARP, NHNOX

ARP, OTC

NBP

OTC

### Step 4: Keep only units regulated by the Acid Rain Program (ARP).

We will limit our observations to facilities regulated by the Acid Rain
Program before the NOx Budget Program. We will use the **filter**
function to keep observations that the variable **Program.s.** equals
**ARP** or **ARP, NBP**. The code is shown below. You just need to run
it.

``` r
df3<-df2 %>%
  filter(Program.s.=="ARP" | Program.s.=="ARP, NBP")
```

### Step 5: Create a new column named **NBP** that is equal to one when each unit is regulated by the NOx Budget Program (3 points).

You will need to combine the **mutate** and **ifelse** functions to
create a dataframe named **df4** with a new column called **NBP**.

**NBP** will equal to 1 if the column **Program.s.** is equal to **ARP,
NBP**. Otherwise, **NBP** will equal to 0.

``` r
df4<-df3 %>%
  mutate(NBP=ifelse(Program.s.=="ARP, NBP",1,0))
```

#### Question 9: How many observations in **df4** were regulated by NBP, and how many were not-regulated by NBP? (1 point for the correct code and 1 point for the correct answer)

``` r
table(df4$NBP)
```


         0      1 
    122193  57849 

#### Answer: 122193 unregulated units, and 57849 regulated units

### Step 6: Click Render to generate an html file of this document. (2 points)

You have reached the end of the assignment. Save the Quarto document and
push the completed assignment back into the GitHub repository.
