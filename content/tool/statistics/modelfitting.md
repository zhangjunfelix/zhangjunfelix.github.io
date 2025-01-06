---
title: "model fitting"
date: 2024-08-16
draft: false

---

## Fitting Linear Mixed-Effects Models (LMMs)

### 1. Factor Treatment Coding

In this example experiment:

- **Independent Variables**:
  1. **A (Face)**: Within-subjects variable with 2 levels.
  2. **B (Number)**: Within-subjects variable with 2 levels.
  3. **C (QUD)**: Between-subjects variable with 4 levels.

- **Response Variable**:  
  Rating on a 7-point scale, used as **numerical values**.

---

### Should You Fit an LMM or an Ordinal Logistic Mixed-Effects Model (Cumulative Link Mixed Model)?

#### Key Considerations:
1. **Nature of Ratings as Numerical Data**:
   - **Continuous**: Assumes equal distances between adjacent points on the scale.
   - **Ordinal**: Assumes ratings are ordered but intervals between points are not equal.

2. **Normality**:
   - Check whether ratings are normally distributed.

#### Methods to Assess Normality:
- **Visual Inspection**: Examine plots (e.g., histograms, Q-Q plots) for deviations from normality.

---

### Handling Missing Data

#### General Approaches:
1. **Remove Missing Data**:
   - Appropriate when missingness is minimal and unlikely to introduce bias.
   - Use this method for MCAR (Missing Completely at Random) data when the proportion of missing data is small (e.g., <5%).

2. **Impute Missing Data**:
   - Consider this if data is MAR (Missing at Random) and retaining more data is important.

3. **Use Models That Handle Missing Data**:
   - Suitable if the analysis framework supports it.

4. **Analyze the Impact of Missing Data**:
   - Evaluate how missing data might influence results to ensure robust conclusions.

#### Missing Data in This Study:
- Missingness is **MCAR (Missing Completely at Random)**.

**Approach**: Remove Missing Data (Listwise Deletion).

---

#### R Code to Remove Missing Data:

1. **Remove Rows with NA Values**:
   ```r
   library(tidyr)
   clean_data <- na.omit(your_data)

2. **Drop Rows Where your_column Contains "na"**:
   ```r
   library(dplyr)
   clean_data <- your_data %>% 
   filter(your_column != "na")




