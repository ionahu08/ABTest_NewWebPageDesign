# Project: Analyze A/B Test Results

This project analyzes the results of an A/B test conducted by an e-commerce website to determine whether the company should adopt a new landing page, retain the existing one, or extend the experiment for further insights.

## Project Overview

The goal of this project is to assess the impact of a new landing page design on conversion rates. This analysis involves hypothesis testing, probability calculations, and regression analysis to make data-driven decisions. The project was part of the Udacity Data Analytics Nanodegree (December 2017 - May 2018).

## Dataset

The dataset used in this project is `ab_data.csv` and contains the following columns:

- **User ID**: Unique identifier for each user.
- **Group**: The treatment group (either 'control' or 'treatment').
- **Landing Page**: The landing page seen by the user (either 'old_page' or 'new_page').
- **Converted**: Whether the user converted (1) or not (0).

### Key Insights from the Dataset:
- **Total number of rows**: 294,478
- **Distinct User IDs**: 290,584
- **Proportion of users converted**:
  - Overall: 11.97%
  - Control Group: 12.04%
  - Treatment Group: 11.88%
- **Number of mismatched rows** (where new_page and treatment don’t line up): 3,839
- **Missing values**: No missing values found.

## Procedures

### Data Preprocessing
1. **Remove rows with mismatched page and treatment group assignments**.
2. **Remove duplicate rows** to ensure accurate analysis.

### Analysis

#### 1. Probability Analysis:
We calculated the probabilities of conversion for each group:
- **Probability of conversion in the control group**: 0.1204
- **Probability of conversion in the treatment group**: 0.1188
- **Overall probability of conversion**: 0.1196
- **Probability of receiving the new page**: 0.5000

#### 2. A/B Testing

##### Hypothesis Testing:
- **Null Hypothesis**: The new page does not result in a higher conversion rate (p_new - p_old ≤ 0).
- **Alternate Hypothesis**: The new page results in a higher conversion rate (p_new - p_old > 0).

##### Approach A: Simulation-based Hypothesis Testing
- We simulated the distribution of the difference in conversion rates under the null hypothesis using 10,000 iterations.
- **Actual Difference**: -0.0016
- **Proportion of simulated differences greater than the observed difference**: 0.9028
- **Conclusion**: The p-value was 0.9, which is large, indicating insufficient evidence to reject the null hypothesis. Therefore, we conclude that there is no significant difference between the old and new page.

##### Approach B: Built-in Statistical Test
- **Z-score**: -1.31
- **P-value**: 0.905
- **Conclusion**: The p-value of 0.91 is higher than the significance level (0.05), indicating that we cannot reject the null hypothesis. Hence, there is no significant difference in conversion rates between the two pages.

#### 3. Regression Analysis
We also performed logistic regression to model the likelihood of conversion based on the landing page and country:
- **P-value for ab_page**: 0.190
- **Conclusion**: The p-value for `ab_page` was greater than 0.05, meaning the effect of the page type on conversion rates is not significant.

## Conclusion

Based on the analysis:
- **A/B Test Results**: There is no significant evidence to suggest that the new landing page performs better than the old one in terms of conversion rates.
- **Country Impact**: No significant impact from the countries (US, CA, UK) on conversion rates was found.
- **Recommendation**: Since the sample size is large, further testing of the new page is unnecessary. The focus should shift to developing a new landing page for testing.

## References
1. [GitHub Repository - Analyze A/B Results](https://github.com/latinacode/Analyze-A-B-Results/tree/master)
2. Udacity Data Analytics Nanodegree Project 4: Analyze A/B Results (December 2017 - May 2018)
