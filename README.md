# Bayesian Modeling for Analyzing the Impact of Education on Global Unemployment Rates

## Overview
This repository provides an analysis of the relationship between education levels and global unemployment rates using Bayesian statistical modeling. The primary objective of this study is to explore how various educational indicators, such as literacy and proficiency in math and reading, influence unemployment rates across different countries. A **Beta Linear Regression** model was developed to identify the most significant educational factors affecting unemployment, employing Markov Chain Monte Carlo (MCMC) methods for estimation.

## Dataset
The dataset used in this analysis is sourced from the **[World Educational Data](https://www.kaggle.com/datasets/nelgiriyewithana/world-educational-data)** on Kaggle. It contains 202 rows and 29 columns, which include variables related to educational attainment, literacy rates, school completion rates, and unemployment. The target variable is **Unemployment Rate**, while 24 independent variables capture different aspects of education at primary, secondary, and tertiary levels.

## Methodology
The core of this analysis is based on Bayesian statistical methods. A **Beta Linear Regression** model was used, which is well-suited for modeling rates and proportions constrained between 0 and 1, such as the unemployment rate. The modeling process incorporated the following steps:

1. **Data Preprocessing**: Features were selected based on relevance to educational outcomes, and missing data were handled using median imputation.
2. **Scaling**: The target variable and relevant features were scaled to ensure model accuracy.
3. **Model Construction**: A Beta Linear Regression model was built using the **RJAGS** library in R, incorporating MCMC methods such as Gibbs Sampling to estimate the posterior distributions of model parameters.
4. **Variable Selection**: Stochastic Search Variable Selection (SSVS) was employed to identify the most impactful educational factors influencing unemployment.

### Bayesian Model Details:
- **Prior Distributions**: Non-informative priors were used for regression coefficients to ensure unbiased estimation.
- **MCMC Sampling**: The model was run with 10,000 burn-in samples and 75,000 iterations, using two chains with a thinning factor of 5.
- **Convergence**: Model convergence was assessed through trace plots, the Gelman-Rubin statistic, and effective sample size (EES).


## Results and Discussion
The Bayesian model has successfully converged, confirmed by a PSRF of 1.01 and an ESS greater than 1000 for all parameters. Based on the Stochastic Search Variable Selection (SSVS), all education-related variables significantly impact unemployment rates. Key findings include:

- Higher out-of-school rates generally increase unemployment probabilities, with some exceptions for certain age groups.
- Completion rates for primary and secondary education show mixed effects, with male completion rates often decreasing unemployment probability.
- Proficiency in math and reading at various education stages has a varying impact, with higher proficiency often linked to lower unemployment probabilities.
- Literacy rates and gross enrollment rates also show significant relationships, with higher values typically reducing unemployment likelihood.
These results highlight the complex relationship between education and unemployment.

### Key Variables:
- **OOSR_Pre0Primary_Age_Male/Female**: Out-of-school rate for pre-primary-aged children (male/female).
- **Completion_Rate_Primary_Male/Female**: Completion rate of primary education (male/female).
- **Proficiency_Math/Reading**: Math and reading proficiency at various stages of education.
- **Youth_15_24_Literacy_Rate_Male/Female**: Literacy rates for youth aged 15-24 (male/female).
- **Unemployment_Rate**: The target variable representing the unemployment rate.

The Bayesian modeling revealed significant insights into how education influences unemployment:

- **Math Proficiency** at early primary levels and **reading proficiency** at the end of primary education were positively correlated with higher unemployment rates.
- Conversely, math proficiency at the end of primary education and reading proficiency in early primary levels were associated with lower unemployment rates.
- For Indonesia, math proficiency at both primary and lower secondary levels was slightly below the global average, suggesting room for improvement to help reduce unemployment.

## Tools Used
- **R** with RJAGS for Bayesian statistical modeling.
- **Python** with Plotly for generating visualizations.
