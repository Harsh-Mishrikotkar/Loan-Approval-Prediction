Loan Approval Prediction
================
Harsh Mishrikotkar
2025-05-20

### Importing libraries and data

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.1.4     ✔ readr     2.1.5
    ## ✔ forcats   1.0.0     ✔ stringr   1.5.1
    ## ✔ ggplot2   3.5.1     ✔ tibble    3.2.1
    ## ✔ lubridate 1.9.4     ✔ tidyr     1.3.1
    ## ✔ purrr     1.0.4     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors
    ## 
    ## Attaching package: 'gridExtra'
    ## 
    ## 
    ## The following object is masked from 'package:dplyr':
    ## 
    ##     combine
    ## 
    ## 
    ## corrplot 0.95 loaded
    ## 
    ## Loading required package: lattice
    ## 
    ## 
    ## Attaching package: 'caret'
    ## 
    ## 
    ## The following object is masked from 'package:purrr':
    ## 
    ##     lift
    ## 
    ## 
    ## Rows: 4269 Columns: 13
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr  (3): education, self_employed, loan_status
    ## dbl (10): loan_id, no_of_dependents, income_annum, loan_amount, loan_term, c...
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

\###Variables

- **no_of_dependents:** How many dependents rely on the loan applicant
- **Education:** Weather the loan applicant has or has not graduated
- **self_employed:** Weather the loan applicant is or is not self
  employed
- **Income_annum:** Annual income of the applicant
- **loan_amount:** Amount of loan application
- **loan_term:** Loan term in years
- **cibil_score:** Credit score
- **residential_assets_value:** Value of residential assets
- **commercial_assets_value:** Value of commercial assets
- **luxury_assets_value:** Value of luxury assets
- **bank_asset_value:** Value of bank assets
- **loan_status:** Weather the loan was approved or rejected

### Data Cleaning

    ##  no_of_dependents  education         self_employed       income_annum    
    ##  Min.   :0.000    Length:4269        Length:4269        Min.   : 200000  
    ##  1st Qu.:1.000    Class :character   Class :character   1st Qu.:2700000  
    ##  Median :3.000    Mode  :character   Mode  :character   Median :5100000  
    ##  Mean   :2.499                                          Mean   :5059124  
    ##  3rd Qu.:4.000                                          3rd Qu.:7500000  
    ##  Max.   :5.000                                          Max.   :9900000  
    ##   loan_amount         loan_term     cibil_score    residential_assets_value
    ##  Min.   :  300000   Min.   : 2.0   Min.   :300.0   Min.   : -100000        
    ##  1st Qu.: 7700000   1st Qu.: 6.0   1st Qu.:453.0   1st Qu.: 2200000        
    ##  Median :14500000   Median :10.0   Median :600.0   Median : 5600000        
    ##  Mean   :15133450   Mean   :10.9   Mean   :599.9   Mean   : 7472617        
    ##  3rd Qu.:21500000   3rd Qu.:16.0   3rd Qu.:748.0   3rd Qu.:11300000        
    ##  Max.   :39500000   Max.   :20.0   Max.   :900.0   Max.   :29100000        
    ##  commercial_assets_value luxury_assets_value bank_asset_value  
    ##  Min.   :       0        Min.   :  300000    Min.   :       0  
    ##  1st Qu.: 1300000        1st Qu.: 7500000    1st Qu.: 2300000  
    ##  Median : 3700000        Median :14600000    Median : 4600000  
    ##  Mean   : 4973155        Mean   :15126306    Mean   : 4976692  
    ##  3rd Qu.: 7600000        3rd Qu.:21700000    3rd Qu.: 7100000  
    ##  Max.   :19400000        Max.   :39200000    Max.   :14700000  
    ##  loan_status       
    ##  Length:4269       
    ##  Class :character  
    ##  Mode  :character  
    ##                    
    ##                    
    ## 

    ##         no_of_dependents                education            self_employed 
    ##                        0                        0                        0 
    ##             income_annum              loan_amount                loan_term 
    ##                        0                        0                        0 
    ##              cibil_score residential_assets_value  commercial_assets_value 
    ##                        0                        0                        0 
    ##      luxury_assets_value         bank_asset_value              loan_status 
    ##                        0                        0                        0

### Graphs of Variables

![](README_files/figure-gfm/Graph%20of%20variables-1.png)<!-- -->

With the histograms and bar charts above: Rejected loan applications
occurred almost guaranteed when the credit score was below approximately
500. Otherwise all the variables have a similar spread between Rejected
and Approved

![](README_files/figure-gfm/Coorelation%20Plot-1.png)<!-- -->

Given the pair plots, we have limits on all variables, with none, other
than the Credit Score having any distinction for any patterns.

    ##           Actual
    ## Predicted  Approved Rejected
    ##   Approved      747       58
    ##   Rejected       49      425

    ## [1] "Accuracy: 0.916340891321345"

    ## [1] "Optimal k: 23"

The KNN model scaled to the normal values has an accuracy of 0.9163 or
91.63%.

This model is accurate as it has an accuracy above 91.63%. This is
enough to belive the model to be accurate.
