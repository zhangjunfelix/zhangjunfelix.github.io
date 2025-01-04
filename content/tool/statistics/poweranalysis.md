---
title: "Power analysis"
date: 2024-08-10
draft: false

---

- [1. notes to Green et al. (2016)](#1-notes-to-green-et-al-2016)
  - [Example dataset](#example-dataset)
    - [step 1: fitting a model](#step-1-fitting-a-model)
    - [step 2: a simple power analysis](#step-2-a-simple-power-analysis)
    - [step 3: running the power analysis](#step-3-running-the-power-analysis)
    - [Increasing the sample size](#increasing-the-sample-size)
    - [Power analysis at a range of sample sizes](#power-analysis-at-a-range-of-sample-sizes)
    - [Varying the number and size of groups](#varying-the-number-and-size-of-groups)
    - [Increasing the size within groups](#increasing-the-size-within-groups)
- [2 Power analysis from scratch](#2-power-analysis-from-scratch)
- [3. Power analysis with `simr` for LMMs](#3-power-analysis-with-simr-for-lmms)
- [4. Power analysis with `simr` for multilevel data](#4-power-analysis-with-simr-for-multilevel-data)
- [5. Power analysis with actual datasets from my own study](#5-power-analysis-with-actual-datasets-from-my-own-study)

## 1. notes to Green et al. (2016)
https://besjournals.onlinelibrary.wiley.com/doi/full/10.1111/2041-210X.12504


- simr works with any LMMs or GLMMs that can be fit with either `lmer` or `glmer` from `LME4`.

- work flow 
   1. a model fitted with LME4 (based on an analysis of data from a pilot study, or create artificial pilot data from scratch )
   2. simulate ***new values for the response variable*** using the model provided; 
   3. refit the model to the simulated response 
   4. apply a statistical test to the simulated fit. 
   
   In this setup the tested effect is known to exist, and so every positive test is a true positive and every negative test is a Type II error. The power of the test can be calculated from the number of successes and failures at step 4.


### Example dataset

The tutorial uses the simdata data set which is included in the package. The data set is representative of environmental monitoring data, with a response variable z (e.g. bird abundance) measured at `10 levels of the continuous fixed effect variable x` (e.g. study year) for `three groups g` (e.g. study site). There is also a continuous response variable y, which is not used in this tutorial.

#### step 1: fitting a model

We start by fitting a very simple `Poisson mixed effects model` in lme4 to the `simdata` data set. In this case we have a random intercept model, where each group (g) has its own intercept but the groups share a common trend.

```
library(simr)
model1 <- glmer(z ~ x + (1|g), family="poisson", data=simdata)
summary(model1)
fixef(model1)
```

    Fixed effects:
                 Estimate Std. Error z value Pr(>¦z¦) 
    (Intercept)  1.54079 0.27173 5.670 1.43e-08 ***
    x            -0.11481 0.03955 - 2.903 0.0037 ** 

The effect size for x is -0.11481. It is significant at the 0.01 level using the default z-test.



#### step 2: a simple power analysis

Suppose that we wanted to replicate this study. If the effect is real, would we have enough power to expect a positive result?

- specifying an effect size
Before starting a power analysis, it is important to consider what sort of effect size you are interested in. Power generally increases with effect size, with larger effects being easier to detect. 

For this example, we will consider the power to detect a slope of −0·05. 

Since this example only focuses on the variable x, We change the size of the fixed effect (i.e., slope) for the variable x from −0·11 to −0·05 (as -0.05 > -0.11),  as follows:

```
fixef(model1)["x"] <- -0.05
```

#### step 3: running the power analysis

```
powerSim(model1)
```

output:
```
## Power for predictor 'x', (95% confidence interval):   
## ***32.40%*** (29.50, 35.40)   
## 
## Test: z-test    
      Effect size for x is -0.050   
## 
## Based on 1000 simulations, (0 warnings, 0 errors)      
## alpha = 0.05, nrow = ***30***    
## 
## Time elapsed: 0 h 2 m 20 s    
```


The power to reject the null hypothesis of zero trend in x is about 33%, given this particular setup. This would almost always be considered insufficient; traditionally 80% power is considered adequate.




#### Increasing the sample size

A small pilot study often will not have enough power to detect a small effect, but a larger study might. 

In simr, the extend function can be used to add rows to a data frame.

The along argument specifies which variable is being extended, and n specifies how many levels to replace it with.

The pilot study had observations at 10 values of x, representing for example study years 1 through 10. In this step, we will calculate the effect of increasing this to 20 years.

```
model2 <- extend(model1, along="x", n=20)
powerSim(model2)
```

output:   
``` 
## Power for predictor 'x', (95% confidence interval):   
##      ***95.50%*** (94.02, 96.70)   
##    
##Test: z-test    
##      Effect size for x is -0.050          
##
## Based on 1000 simulations, (1 warning, 0 errors)     
## alpha = 0.05, nrow = ***60***    
##
## Time elapsed: 0 h 2 m 33 s   
```


#### Power analysis at a range of sample sizes

When data collection is costly, the user might want to collect only as much data as are needed to achieve a certain level of statistical power. The powerCurve function in simr can be used to explore trade-offs between sample size and power.

- Identifying the Minimum Sample Size Required

In the previous example, we found very high power when observations were taken at 20 values of the variable x. Could we reduce that number while keeping our power above the usual 80% threshold?

Use powerCurve(): This function runs powerSim over a range of sample sizes.

```
pc2 <- powerCurve(model2)

print(pc2)

plot(pc2)

```

output: 

https://besjournals.onlinelibrary.wiley.com/cms/asset/250da79b-4849-4cce-b2d3-d7efc050e495/mee312504-fig-0002-m.png



This analysis suggests that the study would have to run for 16 years to have ≥80% power to detect an effect of the specified size.


#### Varying the number and size of groups

In some cases, it is not possible to add number of observations. Thus, increasing the number of study sites or the number of measurements at each site might be a better option. 

In the following codes, we pass the variable _g_ to the _along_ argument and increase it from 3 to 15.

```
model3 <- extend(model1, along="g", n=15)
pc3 <- powerCurve(model3, along="g")
plot(pc3) 
```

output:

https://besjournals.onlinelibrary.wiley.com/cms/asset/2186785e-dd4e-4547-a3a2-d9a2c15862db/mee312504-fig-0003-m.jpg

Therefore, to reach 80% power, we would need at least 11 sites.


#### Increasing the size within groups

use _within_ argument

In model1, each group has only one observation at eachlevel of x and g. We can extend this to 5 observations per site per year. 

```
model4 <- extend(model1, within="x+g", n=5)
pc4 <- powerCurve(model4, within="x+g", breaks=1:5)
print(pc4)

plot(pc4)
```

output of print(pc4):  
```  
## Power for predictor 'x', (95% confidence interval),   
## by number of observations within x+g:   
## 1: 33.90% (30.97, 36.93) - 30 rows    
## 2: 58.00% (54.87, 61.08) - 60 rows    
## 3: 74.40% (71.58, 77.08) - 90 rows    
## 4: 86.30% (84.01, 88.37) - 120 rows    
## 5: 91.80% (89.92, 93.43) - 150 rows    
## 
## Time elapsed: 0 h 11 m 35 s  
```



## 2 Power analysis from scratch

If pilot data is not available, simr can be used to create lme4 objects from scratch as a starting point. 

This requires more paramters to be specified by the user. Values for these parameters might come from the literature or the user’s own knowledge and experience.


- Covariates and parameters

1. First set up some covariates with expand.grid.

```r
x <- rep(1:10)
g <- c('a', 'b', 'c')

X <- expand.grid(x=x, g=g)
```

2. Specify some fixed and random parameters.

```

b <- c(2, -0.1) # fixed intercept and slope

V1 <- 0.5 # random intercept variance

V2 <- matrix(c(0.5,0.05,0.05,0.1), 2) # random intercept and slope 

variance-covariance matrix

s <- 1 # residual variance
```

- Build a model object

1. build an artificial lme4 object

1.1  Use the `makeLmer` function 


```
model1 <- makeLmer(y ~ x + (1|g), fixef=b, VarCorr=V1, sigma=s, data=X)
print(model1)
```

output:
```

## Linear mixed model fit by REML ['lmerMod']   
## Formula: y ~ x + (1 | g)  
##    Data: X  
## REML criterion at convergence: 92.7639   
## Random effects:   
##  Groups   Name        Std.Dev.   
##  g        (Intercept) 0.7071    
##  Residual             1.0000    
## Number of obs: 30, groups:  g, 3    
## Fixed Effects:    
## (Intercept)           x        
##         2.0         -0.1       
```

Use the `makeGlmer` function 

```
model2 <- makeGlmer(z ~ x + (x|g), family="poisson", fixef=b, VarCorr=V2, data=X)
print(model2)
```

output: 
```
## Generalized linear mixed model fit by maximum likelihood (Laplace     
##   Approximation) [glmerMod]           
##  Family: poisson  ( log )           
## Formula: z ~ x + (x | g)            
##    Data: X         
##      AIC      BIC   logLik deviance df.resid          
##  73.5828  80.5888 -31.7914  63.5828       25           
## Random effects:          
##  Groups Name        Std.Dev. Corr         
##  g      (Intercept) 0.7071                     
##         x           0.3162   0.22          
## Number of obs: 30, groups:  g, 3          
## Fixed Effects:          
## (Intercept)            x          
##         2.0         -0.1         
```

- Start the power analysis

Now we have “pilot” models, which can be used with simr.

```
powerSim(model1, nsim=20)
```

```
## Power for predictor 'x', (95% confidence interval):
## 35.00% (15.39, 59.22)
## 
## Test: Kenward Roger (package pbkrtest)
##       Effect size for x is -0.10
## 
## Based on 20 simulations, (0 warnings, 0 errors)
## alpha = 0.05, nrow = 30
## 
## Time elapsed: 0 h 0 m 3 s
```

```
powerSim(model2, nsim=20)
```

```
## Power for predictor 'x', (95% confidence interval):   
## 10.00% ( 1.23, 31.70)  
##     
## Test: z-test    
##       Effect size for x is -0.10   
##     
## Based on 20 simulations, (7 warnings, 0 errors)   
## alpha = 0.05, nrow = 30   
##    
## Time elapsed: 0 h 0 m 4 s    
```


## 3. Power analysis with `simr` for LMMs

In this part of the workshop you will use simr to determine power / required sample size for linear mixed effects models. The lme4 package is used for modelling.

- data

(1) When pilot data or other closely related data are available it is best to use them to obtain estimates for fixed and random effects. 

(2) When that is not possible, creating an appropriate model with parameters specified directly still allows the simulation to be carried out.

  Use information from the literature or previous studies as much as possible. 


- step 1: Create covariates
  
The first step in creating a model for simulation is to create a set of covariates that the model will be based on.

Example study: Children from different *classes* at a *school* will be recruited. Each *participant* will be allocated to either an *intervention or a control* group. For each participant measurements will be taken at *baseline, immediately following the intervention and at follow-up a few weeks later*.

We start by setting up a data frame with *5 classes* and *10 participants* per class.

```
subj <- factor(1:10)      #10 subjects
class_id <- letters[1:5]  #5 classes
time <- 0:2               # 3 test time points
group <- c("control", "intervention")          #2 groups 


subj_full <- rep(subj, 15)  #subj_full这一列10 subjects，每个重复15遍
class_full <- rep(rep(class_id, each=10), 3)  #class_full这一列5 classes，每个重复10遍；然后这50个再重复3遍。
time_full <- rep(time, each=50)  #time_full这一列3 time points，每个重复50遍
group_full <- rep(rep(group, each=5), 15)   #group_full这一列2 groups，每个重复5遍；然后这10个再重复15遍

covars <- data.frame(id=subj_full, class=class_full, treat=group_full, time=factor(time_full))

covars

```

- step 2: specify the parameters for the model

  **y∼treatment+time+treatment×time+(1|class/id)+ϵ**
 
For the purpose of this example parameter values were chosen arbitrarily

based on the above model, the parameters are:       
two fixed effects
 - treat: 2 levels (intervention vs. control)
 - time: 3 levels (time1 vs. time2 vs. time3)    
and random effect

thus, we need to specify the following parameters:
 - one intercept
 - one fixed effect for treat
 - two fixed effect for time
 - two interaction effect between treat and time


```
## Intercept and slopes for intervention, time1, time2, intervention:time1, intervention:time2
fixed <- c(5, 0, 0.1, 0.2, 1, 0.9)

## Random intercepts for participants clustered by class
rand <- list(0.5, 0.1)

## residual variance
res <- 2
```

- create model

The `makeLmer` function from the `simr` package allows us to combine all this information to create a fitted lmer model from scratch.

**`makeLmer`** is for creating a LMM object   
**`makeGlmer`** is for creating a GLMM object

```
model <- makeLmer(y ~ treat*time + (1|class/id), fixef=fixed, VarCorr=rand, sigma=res, data=covars)

model
```

output
```

## Linear mixed model fit by REML ['lmerMod']     
## Formula: y ~ treat * time + (1 | class/id)   
##    Data: covars    
## REML criterion at convergence: 684.4832      
     
## Random effects:     
##  Groups   Name        Std.Dev.     
##  id:class (Intercept) 0.7071    #0.5的平方根  #上面指定的是variance，SD=sqrt(variance)     
##  class    (Intercept) 0.3162        #0.1的平方根    
##  Residual             2.0000      

## Number of obs: 150, groups:  id:class, 50; class, 5     
## Fixed Effects:      
##             (Intercept)        treatintervention                    time1       
##                     5.0                      0.0                      0.1       
##                   time2  treatintervention:time1  treatintervention:time2      
##                     0.2                      1.0                      0.9     
```


- Power analysis

Once you have a fitted lmer model, whether it was fitted to real data or created from scratch, you can use that to simulate new data and assess the required sample size.

The **`powerSim`** function allows us to ***estimate the power to detect a specific effect*** in the model. 

Here we are interested in the effect of the intervention. 

_Since the treatment variable is part of an interaction we will assess its effect by comparing the model specified above to the the alternative model that doesn’t include a treatment variable._ 

We can provide this model alternative via the **`fcompare`** function. This allows us to only specify the fixed effects in the alternative model. 

All random effects will be assumed to be the same as in the original model.

```
sim_treat <- powerSim(model, nsim=100, test = fcompare(y~time))
sim_treat

```

output:
```
## Power for model comparison, (95% confidence interval):      
##       41.00% (31.26, 51.29)       
##       
## Test: Likelihood ratio     
##       Comparison to y ~ time + [re]     
##     
## Based on 100 simulations, (0 warnings, 0 errors)     
## alpha = 0.05, nrow = 150      
##       
## Time elapsed: 0 h 0 m 47 s     
```

notes: 
(1) we can also test for the effect of time in the same way.

```
sim_time <- powerSim(model, nsim=100, test = fcompare(y~treat))
sim_time

```

(2) We can **adjust the effect size** to suit the analysis, e.g. to compute power for an effect size that is smaller than the one observed in a pilot study, or to study power for a range of effect sizes.

e.g.
```
model_large <- model
fixef(model_large)['treatintervention:time1'] <- 2

sim_treat_large <- powerSim(model_large, nsim=100, test = fcompare(y~time))
sim_treat_large

```


- Changing the number of classes used in study

To study the effect an increase in **sample size** has on our ability to detect the effect of interest we can increase the number of levels for one of the factors in our model. 

   **y∼treatment+time+treatment×time+(1|class/id)+ϵ**

This can be achieved with the ***`extend`*** function. For example, we could increase the number of classes from 5 to 20.

```
model_ext_class <- extend(model, along="class", n=20)
model_ext_class

```

We can visualise the effect that **varying the number of classes has on the power to detect the intervention effect** by asking simr to plot a power curve.

```
sim_treat_class <- powerSim(model_ext_class, nsim=100, test = fcompare(y~time))
sim_treat_class

# visualization
p_curve_treat <- powerCurve(model_ext_class, test=fcompare(y~time), along="class")
plot(p_curve_treat)

```

output:   
see: https://humburg.github.io/Power-Analysis/simr_power_analysis.html


- Changing the number of participants per class ‼️

Instead of increasing the number of classes we could ***increase the number of participants per class***. 

This can be achieved with the **`within`** argument to **`extend`**. 

Here we are extending the number of students for each treatment at each time point within each class to 20.

```
model_ext_subj <- extend(model, within="class+treat+time", n=20)
model_ext_subj
```

note:   
**within="class+treat+time"**： extending the number of students for each treatment at each time point 

```
# a power estimate at the increased sample size as well as a power curve that combines estimates at different sample sizes

sim_treat_subj <- powerSim(model_ext_subj, nsim=100, test = fcompare(y~time))

sim_treat_subj


# visualization

p_curve_treat <- powerCurve(model_ext_subj, test=fcompare(y~time), within="class+treat+time", breaks=c(5,10,15,20))
plot(p_curve_treat)

```

- Changing number of classes and participants per class

We may want to study models with changes to **multiple sample size** components. The relevant changes can be applied to the model successively.

```
model_final <- extend(model, along="class", n=8)

model_final <- extend(model_final, within="class+treat+time", n=20)

sim_final <- powerSim(model_final, nsim=100, test = fcompare(y~time))

sim_final
```

output:   
```
Power for model comparison, (95% confidence interval):
      97.00% (91.48, 99.38)

Test: Likelihood ratio
      Comparison to y ~ time + [re]

Based on 100 simulations, (2 warnings, 0 errors)
alpha = 0.05, nrow = 960

Time elapsed: 0 h 0 m 28 s
```


以下为ZJ所加：

```
# visualization

p_curve_final <- powerCurve(model_final, nsim = 100, test=fcompare(y~time), within="class+treat+time", breaks=c(5,10,15,20))

plot(p_curve_final)

```

output:
```
Power for model comparison, (95% confidence interval),
by number of observations within class+treat+time:
      5: 72.00% (62.13, 80.52) - 240 rows
     10: 92.00% (84.84, 96.48) - 480 rows

Time elapsed: 0 h 0 m 34 s
```

## 4. Power analysis with `simr` for multilevel data

https://rstudio-pubs-static.s3.amazonaws.com/484106_6b51212f20164fdd88cd7cce89bdef79.html


Example study: - Pupils from different classes will be recruited. 
- Pupil level predictor: extraversion (continuous)
- Class level predictor: teacher experience  (continuous)
- Outcome variable: pupil popularity  (continuous)

```
library(lme4)
library(MonteCarlo)
library(dplyr)
library(ggplot2)
library(afex)
library(simr)
library(pwr)
library(broom) #extract random effects
library(knitr)
library(truncnorm)

```


```
data <- read.delim('popular2.dat', header = TRUE, sep="", skip=2, as.is=TRUE)

#提取该数据集中第1、2、4、5、6、7列的数据
data<-data[,c(1,2,4,5,6,7)]

#将这六列进行命名
names(data) <- c("class","pupil","extrav","sex","texp","popular")

#计算gmc
# gmc的好处：Grand Mean Centering通过将每个观测值减去其所在变量的总均值，   
可以减少变量之间的相关性，从而减轻多重共线性的影响；通过将低层次变量进行总均值中心化，     
可以分离出低层次变量的组内变异（within-group variation）和组间变异   
（between-group variation），从而更准确地分析不同层次变量之间的交互作用。

df <- data %##% 
  # Grand mean centering
  mutate(extrav.gmc = extrav-mean(extrav)) %##%
  mutate(texp.gmc = texp-mean(texp)) %>%
  mutate(popular.gmc = popular-mean(popular))

#imagine we only have pilot data from 10 classes, we will create simulated model based on parameters from these pilot data.
#logic to select 10 classes in random

# set.seed(12345)
# class_unique<-data.frame(unique(df$class))
# class_sample<-sample_n(class_unique,20,replace=FALSE)
# 
# #logic to select all subjects in these classes
# df<-df%>%
#   filter(class %in% class_sample$unique.df.class.)

cols<-c('class','pupil',"sex")
data[cols]<-lapply(data[cols],factor)

kable(head(df))

```

- Changing number of clusters while holding Ss per cluster = 10

```
#logic to select 10 subjects from each of these randomly selected classes
set.seed(0)

df_10<-df%>%
  group_by(class)%>%
  sample_n(size=10)
```

- Fit lmer model

```
m<-lmer(popular.gmc~extrav.gmc*texp.gmc+
                (1|class),df_10,REML=FALSE)

summary(m)
```

- Extract parameter estimates from lmer model

```
# parameters #1: fixed intercept and slope
fixed <- c(-.0805,.4875,.1078,-.02224) 

# parameters #1: random intercept and slope variance-covariance matrix
# For class
rand <-.4013

# parameters #3: Exrtact the residual sd  
# ^ 为幂运算，如8^ = 8 * 8 =64；^.5 = square root
s <- .8824^.5 

```

- Create Simulated model using extracted parameters

```

model <- makeLmer(y ~ extrav*texp + (1|class), fixef=fixed, VarCorr=rand, sigma=s, data=df_10)
model

```

output:

```
## Linear mixed model fit by REML ['lmerMod']     
## Formula: y ~ extrav * texp + (1 | class)     
##    Data: df_10     
## REML criterion at convergence: 2911.247     
     
## Random effects:     
##  Groups   Name        Std.Dev.     
##  class    (Intercept) 0.6335       
     
##  Residual             0.9394       
## Number of obs: 1000, groups:  class, 100     
     
## Fixed Effects:     
## (Intercept)       extrav         texp  extrav:texp       
##    -0.08050      0.48750      0.10780     -0.02224     
```


- Changing the number of classes

To study the effect **an increase in sample size** has on our ability to detect **the effect of interest** we can **increase the number of levels for one of the factors** in our model. 

This can be achieved with the **`extend`** function. 

For example, we could increase the number of classes from 10 to 50, this way we can do power analysis for any number of clusters that is less than 50.

```
model_ext_class <- extend(model, along="class", n=50)   
model_ext_clas

```

- Power curve of **pupil extraversion**

Here we test how **number of clusters(ZJ: grouping factor)** effect the power of **extraversion** (one of the two fixed variables).

_以下code中请注意 test(), along 等arguments

```
set.seed(0)
p_curve_extrav <- powerCurve(model_ext_class, 
                            test=fcompare(y~texp), 
                            along="class",
                            breaks=c(10,15,20,30,50),
                            nsim=500,alpha=.05, progress=FALSE)


# visualization
plot(p_curve_extrav)

```

![power curve of number of classes (50) on the power of pupil extraversion](/images/pupilextracurve.png "power curve of number of classes (50) on the power of pupil extraversion")

This curve represents the power estimations of pupil extraversion when **nsize = 10 ("10 subjects from each class") and cluster size varies**. 

We need **at least 20 clusters(classes) of 10 (subjects) to have a power of at least 80% given the effect is present**.


- Power curve of teacher experience

Here we test how number of clusters ("50") affect the power of teacher experience.

```
set.seed(0)
p_curve_texp <- powerCurve(model_ext_class, 
                            test=fcompare(y~extrav), 
                            along="class",
                            breaks=c(10,15,20,30,50),
                            nsim=500,alpha=.05, progress=FALSE)

#visualization

plot(p_curve_texp)

```

output

![power curve of number of classes (50) on the power of teacher experience](/images/texpcurve.png "power curve of number of classes (50) on the power of teacher experience")

This curve represents the power estimations of the cross-level interaction between extraversion and teacher experience when **nsize = 10 and cluster size varies**. 

We need **at least 45 clusters(classes) of 10 (subjects) to have a power of at least 80% given the effect is present**.


- Power curve of interaction between extraversion and teacher experience

Here we test how number of clusters affect the power of inetaction between extravtion and teacher experience.

```
set.seed(0)
p_curve_interaction <- powerCurve(model_ext_class, 
                            test=fcompare(y~texp+extrav), 
                            along="class",
                            breaks=c(10,15,20,30,50),
                            nsim=500,alpha=.05, progress=FALSE)

```

note: test = fcompare(y~texp+extrav)

output

![power curve of number of classes (50) on the power of interaction between extraversion and teacher experience](/images/extratexpcurve.png "power curve of number of classes (50) on the power of interaction between extraversion and teacher experience")


This curve represents the power estimations of the cross-level interaction between extraversion and teacher experience when nsize = 10 and cluster size varies. 

We need **at least 42 clusters of 10 to have a power of at least 80% given the effect is present**.


* ZJ's summary (# of subject = 10)

(1) for the variable of **pupil exterversion**, this factor reaches 80% of power when there are at least 20 classes, namely, 20 classes * 10 subjects/class = **200 observations**
(2) for the variable of **teacher experience**, this factor reaches 80% of power when there are at least 45 classes, namely, 45 classes * 10 subjects/class = **450 observations**
(3) for the **interaction between pupil exterversion and teacher experience**, this factor reaches 80% of power when there are at least 42 classes, namely, **42 classes * 10 subjects/class = 420 observations**


- Changing number of clusters while holding Ss per cluster = 15

```
#logic to select 10 subjects from each of these randomly selected classes
set.seed(0)

df_15<-df%>%
  group_by(class)%>%
  sample_n(size=15)   #15 subjects from each class

```

-- Fit lme model

```
m2<-lmer(popular.gmc~extrav.gmc*texp.gmc+
                (1|class),df_15,REML=FALSE)

summary(m2)

```

note: here `gmc` is used


-- Extract parameter estimates from lmer model

```
# fixed intercept and slope
fixed2 <- c(-.0655,.4794,.1071,-.02539) 

# random intercept and slope variance-covariance matrix
# For class
rand2 <-.3682

# Exrtact the residual sd
s2 <- .8908^.5 

```

-- Create Simulated model using extracted parameters

```
model2 <- makeLmer(y ~ extrav*texp + (1|class), fixef=fixed2, VarCorr=rand2, sigma=s2, data=df_15)
model2
```

-- Changing the number of classes

```
model_ext_class2 <- extend(model2, along="class", n=50)
model_ext_class2

```

-- Power curve of pupil extraversion

```
set.seed(0)
p_curve_extrav2 <- powerCurve(model_ext_class2, 
                            test=fcompare(y~texp), 
                            along="class",
                            breaks=c(10,15,20,30,50),
                            nsim=500,alpha=.05, progress=FALSE)


plot(p_curve_extrav2)

```

output
![power curve of number of classes (50) on the power of pupil extraversion when nsubject = 15](/images/pupilextracurve2.png "power curve of number of classes (50) on the power of pupil extraversion when nsubject = 15")

This curve represents the power estimations of pupil extraversion when nsize = 15 and cluster size varies. 

We need **at least 15 clusters of 15 to have a power of at least 80% given the effect is present**.

-- Power curve of teacher experience

```
set.seed(0)
p_curve_texp2 <- powerCurve(model_ext_class2, 
                            test=fcompare(y~extrav), 
                            along="class",
                            breaks=c(10,15,20,30,50),
                            nsim=500,alpha=.05, progress=FALSE)

plot(p_curve_texp2)

```

output:

![power curve of number of classes (50) on the power of teacher experience when nsubject = 15](/images/texpcurve2.png "power curve of number of classes (50) on the power of teacher experience when nsubject = 15")

This curve represents the power estimations of teacher experience when nsize = 15 and cluster size varies. 

We need **at least 18 clusters of 15 to have a power of at least 80% given the effect is present**.


-- Power curve of interaction between extraversion and teacher experience

```
set.seed(0)
p_curve_interaction2 <- powerCurve(model_ext_class2, 
                            test=fcompare(y~texp+extrav), 
                            along="class",
                            breaks=c(10,15,20,30,50),
                            nsim=500,alpha=.05, progress=FALSE)

plot(p_curve_interaction2)

```

output:

![power curve of number of classes (50) on the power of interaction between extraversion and teacher experience when nsubject = 15](/images/extratexpcurve2.png "power curve of number of classes (50) on the power of interaction between extraversion and teacher experience when nsubject = 15")

This curve represents the power estimations of the cross-level interaction between extraversion and teacher experience when nsize = 15 and cluster size varies. 

We need **at least 20 clusters of 15 to have a power of at least 80% given the effect is present**.


* ZJ's summary (# of subject = 15)

(1) for the variable of **pupil exterversion**, this factor reaches 80% of power when there are at least 15 classes, namely, 15 classes * 15 subjects/class = **225 observations**  

(2) for the variable of **teacher experience**, this factor reaches 80% of power when there are at least 18 classes, namely, 18 classes * 15 subjects/class = **270 observations**    

(3) for the **interaction between pupil exterversion and teacher experience**, this factor reaches 80% of power when there are at least 20 classes, namely, **20 classes * 15 subjects/class = 300 observations**   

* conclusion    
We need **at least 20 (clusters) x 15 (Ss/cluster) = 300 observations** to detect all 3 effects (extrav, texp, extrav x texp) given that all 3 effects exist in the population. 



===============================================================   

_The following is a walk-through based on my own studies._


## 5. Power analysis with actual datasets from my own study


Study #1: response elicitation

1. overview of the study   
 
independent variables:   
two within-subjects variables (A & B), each with 2 levels (A1, A2, B1, B2) 
four conditions

dependent variable:   
counts of responses (6 types in total based on the pilot study)
(types of responses that participants give in different conditions)     


2. pilot dataset
   50 subjects

3. fit a model for count data 
   
Based on the types of variables, multinomial logistic models should be used. 











