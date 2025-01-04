---
title: "Data types, distribution, modeling choices"
date: 2023-08-09
draft: false

---



## Data types, distribution, modeling choices

Linear Mixed Effects Models (LMMs) and Generalized Linear Mixed Effects Models (GLMMs) 

The choice between LMMs and GLMMs depends on the nature of your response variable and the specific goals of your analysis.

A summary of data types, their distribution, link functions, and modeling choices
| data type    | normality  | distribution | model type                                                         | link function                           | example data                                                            |
|--------------|------------|--------------|--------------------------------------------------------------------|-----------------------------------------|-------------------------------------------------------------------------|
| continuous   | normal     | normal       | LMMs                                                               | identity (normally not specify in LMMs) | reaction times                                                          |
| binary       | non-normal | binomial     | GLMMs                                                              | logit                                   | binary outcome: pass/fail                                               |
| count        | non-normal | poisson      | GLMMs                                                              | log                                     | number of events                                                        |
| proportional | non-normal | binomial     | GLMMs                                                              | logit                                   | proportion of seeds that germinate under different treatment conditions |
| categorical  | non-normal | multinomial  | GLMMs                                                              | logit                                   |                                                                         |
| ordinal      | non-normal | cumulative   | ordinal logistic mixed-effects model/  cumulative link mixed model | cumulative logic                        |                                                                         |

### - WHEN TO USE
Use LMMs when your response variable is **continuous** and is assumed to follow a **normal distribution**.    
Use GLMMs when your response variable is **not continuous** and does **not follow a normal distribution**. 

### -  EXAMPLE SCENARIOS
#### 1. LMMs
- Repeated Measures on **Continuous Outcomes**    
Suppose you're conducting an experiment where participants' reaction times (a continuous variable) are measured under different conditions (e.g., different levels of a stimulus). Each participant is measured multiple times.
    
Here, you might be interested in whether the stimulus level affects reaction time while accounting for individual differences in baseline reaction time. An LMM would allow you to model reaction time as a function of stimulus level (fixed effect) while accounting for random variability between participants (random effect).

- Growth Curve Analysis:    
Imagine a study where children's reading abilities (measured on a continuous scale) are assessed at multiple time points. You want to analyze how reading ability changes over time, considering that children may have different starting points and growth rates.
    
An LMM can model the change in reading ability over time (fixed effect) while accounting for individual differences in starting points and growth rates (random effects).

#### 2. GLMMs

- When to Use a GLMM     
**Hierarchical Data Structure**: Use GLMM when your data has a hierarchical or nested structure. For example, students nested within classrooms, or repeated measures from the same subjects over time.    
**Non-Normal Response Variables**: GLMMs are ideal when your response variable does not follow a normal distribution. They handle various types of response distributions:

> **Binary outcomes** (e.g., success/failure) using a binomial distribution.
> **Counts** (e.g., number of events) using a Poisson distribution.
> **Proportions** using a binomial distribution.
> **Multinomial outcomes** (e.g., categorical data with more than two levels).
Random Effects: When there is a need to model random effects, such as variability among subjects, items, or clusters, GLMMs allow you to account for this variability. This is essential when the assumption of independence between observations is violated.

Complex Experimental Designs: GLMMs are useful in experiments with complex designs that include both fixed effects (e.g., treatment effects that are the main focus of your study) and random effects (e.g., random variability due to subjects, items, etc.).

Repeated Measures: When you have repeated measures from the same subjects over time or under different conditions, GLMMs can model the correlation between these repeated measures.





2.1 Binary Outcomes (Logistic Mixed Model)   

Suppose you're studying the effect of a new teaching method on whether students pass or fail an exam (binary outcome: pass/fail). You have data from multiple schools, with students nested within schools.
    
A GLMM with a binomial distribution and logit link function can be used to model the probability of passing based on the teaching method (fixed effect) while accounting for variability between schools (random effect).
        
> - **Binomial Distribution**  
> The binomial distribution is a discrete probability distribution that models the number of successes in a fixed number of independent trials of a **binary (yes/no) experiment**. Each trial has two possible outcomes: success or failure, with a constant probability of success.

> - Key Characteristics:  
> -- Number of Trials (n): The experiment is repeated a fixed number of times.   
> -- Probability of Success (p): Each trial has the same probability of success    
> -- Number of Successes (k): The distribution describes the probability of obtaining a specific number of successes in 𝑛 trials.

> - **logit link function**   
> -- The logit link function is used in logistic regression, where the response variable is binary (e.g., success/failure, yes/no).    
> -- It models the log-odds of the probability of an event occurring as a linear function of the predictor variables.   
> -- The coefficients in a logistic regression model using the logit link function represent the change in the log-odds of the outcome for a one-unit change in the predictor variable.

> - Example 1: Medical Study (Predicting Disease Presence)  
> -- In a medical study, researchers might be interested in predicting whether a patient has a certain disease (1) or does not have it (0) based on several predictor variables like age, blood pressure, and cholesterol levels.   
> -- Response Variable: Disease (binary outcome: 0 = No, 1 = Yes)    
> -- Predictor Variables: Age, Blood Pressure, Cholesterol Level   

 ![Example data format for binary data/binomial distribution](/images/Binarydata.png "Example data format for binary data/binomial distribution")
    

2.2 Count Data (Poisson Mixed Model)

Consider a study on the number of errors made by workers in a factory over different shifts. The response variable is the **count** of errors, which is **not normally distributed** and likely follows a **Poisson distribution**.
    
A GLMM with a Poisson distribution and log link function can model the number of errors as a function of shift type (fixed effect) while accounting for variability between workers (random effect).

> - **Poisson distribution**   
> It is a discrete probability distribution that models the **number of events** occurring within a fixed interval of time, space, or any other continuous domain. It is used when events occur independently and the average rate (mean number of events) is constant.

> - Example scenarios     
> -- Number of Emails Received: The number of emails you receive per hour can be modeled by a Poisson distribution if emails arrive randomly and independently of each other.   
> -- Traffic Accidents: The number of traffic accidents at a particular intersection per month may follow a Poisson distribution if accidents occur randomly.   
> -- Phone Calls to a Call Center: The number of calls received by a call center in a given time period (e.g., per hour) can be modeled using a Poisson distribution if the calls are independent and the rate of calls is constant.  

> - **log Link Function**   
> -- When modeling **count data** using the **Poisson distribution** in a regression context, the most appropriate link function is the **log link function**.  
> -- The log link function relates the expected count (mean 𝜆) to a linear combination of the predictor variables.   
> -- The coefficients in a Poisson regression model using the log link function represent the change in the log of the expected count for a one-unit change in the predictor variable.   


> - **Example data format**

> You are studying the number of correct answers students give in a quiz, with quizzes given on multiple occasions. Each student takes the quiz multiple times under different conditions (e.g., time of day, difficulty level).

> - Count Data (Response Variable): Correct_Answers (number of correct answers).   
> - Fixed Effects: Time_of_Day (categorical variable: Morning, Afternoon) and Difficulty (categorical variable: Easy, Hard).    
> - Random Effects: Student_Random, accounting for differences in quiz performance between students.    
> - Grouping Variable: Student_ID, the identifier for each student.

 ![Example data format for count data/poisson distribution](/images/Count-poissondata.png "Example data format for count data/poisson distribution")



2.3 Proportional Data

Imagine you're analyzing the _proportion of seeds that germinate under different treatment conditions_, where each condition has several batches of seeds. The response is the proportion of seeds germinated, which follows a binomial distribution.

A GLMM with a **binomial distribution** and **logit link function** can be used to model the proportion of germination based on treatment (fixed effect) while accounting for batch-to-batch variability (random effect).


> Here’s an example data frame for proportional data where we might use a GLMM to analyze the effect of different conditions on proportions, with random effects for different groups or subjects.

![Example data format for proportional data/binomial distribution](/images/Proportionaldata.png "Example data format for proportional data/binomial distribution")

2.4 Multinomial Outcomes

Suppose you're interested in modeling the choice of transportation mode (car, bus, bike, walk) among commuters, with **multiple choices** available **(categorical outcome)**. Commuters are nested within cities.

Multinomial outcomes involve **categorical variables** where each category represents a distinct, non-ordinal option. When you have more than two categories, and each observation falls into one of these categories, you are dealing with a multinomial distribution.

Multinomial Logistic Regression is **an extension of logistic regression** used when the outcome variable has **more than two categories**. It models the probability of each category relative to a reference category.

A GLMM with a **multinomial distribution** can model the probability of choosing each transportation mode based on factors like distance or cost (fixed effects), while accounting for variability between cities (random effect).


- Link function for multinomial distribution

For a multinomial distribution, the most common link function used is the **logit link function**, which is applied in the context of multinomial logistic regression.

- Example of Multinomial Outcomes   

A dataframe for multinomial outcomes would include a categorical dependent variable with more than two levels (categories), and potentially several predictors. Here’s an example dataframe where the categorical outcome is the type of product purchased, and the predictors include customer demographics and purchase history.  

Let's assume a scenario where you are analyzing customers' choice of product category from four possible options: Electronics, Clothing, Furniture, and Books.


![Example data format for multiple categorical data/multinomial distribution](/images/Categoricaldata.png "Example data format for multiple categorical data/multinomial distribution")

Modeling:

Dependent Variable: Purchase_Category (categorical with multiple levels).   
Predictors: Age, Income, Gender

`model <- multinom(Purchase_Category ~ Age + Income + Gender, data = your_dataframe)`

   
2.5 ordinal data

Ordinal data has a natural order but the intervals between levels are not necessarily equal.

When dealing with ordinal data in the context of mixed effects modeling, you typically use an **ordinal logistic mixed-effects model** (also known as the **_cumulative link mixed model_**). This model accounts for the ordinal nature of the response variable and incorporates both fixed and random effects.

- Link Function: Cumulative logit link function

- Example Scenario

Imagine you are studying customer satisfaction with a product, measured on a 5-point ordinal scale:

1 (Very Dissatisfied)   
2 (Dissatisfied)   
3 (Neutral)   
4 (Satisfied)   
5 (Very Satisfied)  

You want to analyze how customer satisfaction is influenced by age and income, while accounting for variability between different stores where the survey was conducted.

![Example data format for ordinal data/cumulative distribution](/images/ordinaldata.png "Example data format for ordinal data/cumulative distribution")


>>> Model Specification   
Fixed Effects: Age and Income.   
Random Effects: Store_ID (to account for variability between stores).   

    model <- clmm(Satisfaction ~ Age + Income + (1 | Store_ID), data = your_data)



#### 3. different types of data distribution

Understanding different distributions and their applications in real-world scenarios is key to choosing the appropriate statistical model. Below are explanations of common distributions with concrete examples:

3.1 Normal Distribution  
Description: Symmetrical, bell-shaped distribution where most data points are clustered around the mean. It's defined by the mean (average) and standard deviation (spread). 

- Example:

> Heights of Adults: The heights of adult men in a large population typically follow a normal distribution. Most men have a height close to the average (e.g., 5'9" or 175 cm), with fewer men being significantly shorter or taller.  

> Test Scores: In standardized tests, scores are often designed to follow a normal distribution, with most students scoring around the mean and fewer achieving very high or very low scores.

3.2 Binomial Distribution  
Description: Discrete distribution representing the number of successes in a fixed number of independent trials, with each trial having the same probability of success.

- Example:

> Flipping a Coin: If you flip a fair coin 10 times, the number of heads you get follows a binomial distribution. Each flip is independent, and the probability of getting heads is 0.5.

> Pass/Fail Outcomes: In a classroom, if a teacher randomly selects 5 students and checks if they passed an exam, the number of students who passed (out of 5) follows a binomial distribution.

3.3. Poisson Distribution
Description: Discrete distribution representing the number of events occurring in a fixed interval of time or space, where events occur independently at a constant average rate.

- Example:

> Calls to a Call Center: The number of phone calls received by a call center in an hour might follow a Poisson distribution. If the average number of calls per hour is 20, the distribution describes how many calls might be received in any given hour.

> Traffic Accidents: The number of traffic accidents at a particular intersection in a month could follow a Poisson distribution, assuming accidents occur randomly over time.

3.4. Exponential Distribution
Description: Continuous distribution describing the time between events in a Poisson process, where events occur continuously and independently at a constant average rate.

- Example:

> Time Between Bus Arrivals: The time between arrivals of buses at a bus stop might follow an exponential distribution. If buses arrive on average every 10 minutes, the distribution describes the likelihood of waiting times between buses.

> Lifespan of Light Bulbs: The time until a light bulb burns out can be modeled by an exponential distribution, assuming the failure rate is constant over time.

5. Uniform Distribution
Description: Continuous or discrete distribution where all outcomes are equally likely within a specified range.

- Example:

> Rolling a Fair Die: Rolling a fair six-sided die follows a discrete uniform distribution, where each face (1 through 6) has an equal probability of occurring (1/6).

> Random Number Generation: If a computer program generates random numbers between 0 and 1, these numbers follow a continuous uniform distribution, where any number in the range [0, 1] is equally likely.

3.6. Bernoulli Distribution
Description: A special case of the binomial distribution for a single trial, representing a random experiment with exactly two possible outcomes: success (1) or failure (0).

- Example:

> Coin Flip: The outcome of a single coin flip (heads or tails) follows a Bernoulli distribution, with a probability 𝑝 of success (e.g., heads).

> Defective Product Check: Testing a single product from a manufacturing line to see if it is defective (defective or not defective) follows a Bernoulli distribution.

3.7. Multinomial Distribution
Description: Generalization of the binomial distribution to more than two outcomes, representing the probabilities of different categories in multiple trials.

- Example:

> Dice Rolls: Rolling a fair six-sided die 10 times, where the outcome is a category (1 through 6), follows a multinomial distribution. The distribution describes the number of times each face appears in 10 rolls.

> Survey Responses: In a survey where respondents choose among several options (e.g., "Agree," "Neutral," "Disagree"), the number of respondents selecting each option in a sample follows a multinomial distribution.

3.8. Negative Binomial Distribution
Description: Discrete distribution representing the number of failures before a specified number of successes occurs in a sequence of independent and identically distributed Bernoulli trials.

- Example:

> Customer Complaints: If you're studying the number of dissatisfied customers (failures) you encounter before getting 10 satisfied customers (successes), the number of dissatisfied customers follows a negative binomial distribution.

> Sales Success: A salesperson might record the number of unsuccessful sales calls before securing a certain number of sales. This scenario can be modeled using a negative binomial distribution.

3.9. Log-Normal Distribution
Description: A distribution of a random variable whose logarithm is normally distributed. It is skewed and often used to model positive data.

- Example:

 > Income Distribution: Individual incomes in an economy often follow a log-normal distribution because income cannot be negative and tends to be right-skewed, with many people earning less and a few earning much more.

 > Stock Prices: The price of stocks over time can follow a log-normal distribution, as prices are multiplicative and cannot fall below zero.


| **Data Type**             | **Typical Distributions**                       | **Modeling Choices**                       | **Description**                            |
|---------------------------|-------------------------------------------------|--------------------------------------------|--------------------------------------------|
| **Continuous**            | 
|---------------------------|- Normal (Gaussian)                             | - Linear Regression                        | - Continuous values (e.g., height)         |
|---------------------------| - Exponential                                   | - Exponential Regression                   | - Time until event (e.g., time to failure) |
|---------------------------| - Uniform                                       | - Non-Parametric Methods                   | - Evenly distributed values                |
|---------------------------| - Log-normal                                    | - Log-Linear Models                        | - Logarithmically normal (e.g., income)    |
|---------------------------| - Gamma                                         | - Gamma Regression                         | - Waiting times/life durations             |
|**Discrete**                                    |                                             |                                            |
|---------------------------| - Binomial                                      | - Logistic Regression                      | - Successes in trials                      |
|---------------------------| - Poisson                                       | - Poisson Regression                       | - Events in interval                       |
|---------------------------| - Geometric                                     | - Geometric Regression                     | - Trials until first success               |
| **Categorical (Nominal)**                       |                                             |                                            |
|---------------------------| - Multinomial                                   | - Multinomial Logistic Regression          | - Non-ordered categories (e.g., fruit types)|
|---------------------------| - Categorical                                   | - Chi-Square Tests, Logistic Regression    | - Categorical counts/proportions           |
| **Categorical (Ordinal)**                       |                                             |                                            |
|---------------------------| - Ordinal Logistic                              | - Ordinal Logistic Regression              | - Ordered categories (e.g., satisfaction)  |
|---------------------------| - Proportional Odds                             | - Proportional Odds Model                  | - Effect constant across levels            |
| **Binary (Dichotomous)**                        |                                             |                                            |
|---------------------------| - Bernoulli                                     | - Binary Logistic Regression               | - Two outcomes (e.g., yes/no)              |
|---------------------------| - Binomial                                      | - Logistic Regression                      | - Successes in Bernoulli trials            |
| **Count**                                       |                                             |                                            |
|---------------------------| - Poisson                                       | - Poisson, Negative Binomial Regression    | - Number of events                         |
|---------------------------| - Negative Binomial                             | - Negative Binomial Regression             | - Over-dispersed counts                    |
| **Proportion**                                  |                                             |                                            |
|---------------------------| - Binomial                                      | - Logistic, Beta Regression                | - Successes/total trials                   |
|---------------------------| - Beta                                          | - Beta Regression                          | - Continuous proportions (0 to 1)          |
| **Time-to-Event**                               |                                             |                                            |
|---------------------------| - Exponential                                   | - Survival Analysis                        | - Time until event occurs                  |
|---------------------------| - Weibull                                       | - Parametric Survival Models               | - Survival times, varying rates            |
|---------------------------| - Cox Proportional Hazards                      | - Cox Proportional Hazards Model           | - Time-to-event with censored data         |


some references:

https://rcompanion.org/handbook/H_08.html
Summary and Analysis of Extension Program Evaluation in R