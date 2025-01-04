---
title: "model fitting"
date: 2024-08-16
draft: false

---

## fitting lMMs

1. factor treatment coding

In this example experiment, there are three independent variables. A (face) and B (number) are within-subjects variables, each having two levels. C (QUD) is a between-subject variable and has four levels.

Response variable is rating on a 7-point scale. 

I use the ratings as numerical values. 

* fitting LMM or ordinal logistic mixed-effects model/cumulative link mixed model?

factors to consider
-- nature of ratings as numerical data: continuous (equal distance between adjacent points on the scale) vs. ordinal (ratings are ordered but intervals between adjecent points are not assumed to be equal)
-- normality: normally distributed
  methods to assess normality

(1) Visual Inspection

-- handling of missing datapoints
Remove Missing Data if missingness is minimal and unlikely to introduce bias.   
Impute Missing Data when you want to retain more data and believe the data is MAR.    
Use Models That Handle Missing Data if appropriate for your analysis and missing data structure.     
Analyze the Impact of Missing Data to ensure your conclusions remain robust.     

in this study, Missingness is unrelated to any observed or unobserved data (MACR)

Remove Missing Data (Listwise Deletion)

When to Use: When the proportion of missing data is small (e.g., less than 5%) and you believe the data is MCAR.

In R, you can use na.omit() to remove rows with NA values (if missing datapoints are left blank).

```
library(tidyr)
clean_data <- na.omit(your_data)
```

or, Drop rows where `your_column` contains "na"
```
     library(dplyr)
     clean_data <- your_data %>% 
     filter(your_column != "na")

```


-- bar plotting
(1) plot Histograms by Condition



(2) plot Density Plots by Condition

(3) 



