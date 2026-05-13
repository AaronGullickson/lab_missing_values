---
editor: visual
---

# Missing Values Lab

This repository contains data from the 2020 [Coperative Election Study](https://cces.gov.harvard.edu/). We will be looking at how the relationship between party affiliation and political ideology (conservative-liberal) is different by race, gender, and education. To do this, we will run the following set of three models.

1.  A baseline model which predicts the conservative ideology (on a scale of 1 to 5) of respondents based on party affiliation.
2.  Add race, gender, education, income, and religiosity as variables to model 1. This allows us to both see how these variables affect the likelihood of conservative ideology and how much they might account for the relationship between conservative ideology and party affiliation in model 1.
3.  Add an interaction term to model 2 between party affiliation and race. This will tell you whether the relationship between party affiliation and ideology is weaker or stronger for certain racial groups.

## Dealing with missing values

To run these models we need to deal with missing values on some of the variables. This is a two-part process. First, you will need to identify and properly code missing values in the `organize_data.qmd` script. Then you will need to explore how the results vary depending on the method you use to address them in `analysis.qmd`.

### Organizing the data

We will use the following variables from the CES:

- ideo5 - the political ideology variable, scored on a scale where higher values mean more conservative beliefs. Its a five point scale, but you will notice there are six unique values. What is going on here?

- pid3 - party affiliation as Republican, Democrat, Independent, or Other.

- race - Racial identification.

- gender - Reported gender of the respondent

- educ - educational level of the respondent

- faminc_new - Family income in brackets. We will just use it as a quantitative score.

- pew_religimp - How important is religion in a respondent's life on a four point scale. Treat as a categorical variable.

Some missing values are already coded in the raw CES file. However, other missing values are coded with a numeric value. For each of the variables used in the `organize_data.qmd` script, you need to use the codebook provided in the `data/data_raw` directory to identify any numeric codes corresponding to missing values and properly encode them.

As part of this process, you will also need to turn several of the variables into categorical variables as they will by default all be represented as numeric integers. Technically, family income (`faminc_new`) is recorded in brackets, but we will just leave it as a numeric value for simplicity. We will also leave `ideo5` as a numeric value since that is our dependent variable.

Once you have completed this process, you can save the final dataset to the `data/data_constructed` directory, using the provided code.

### Running the models

The `analysis.qmd` file contains some starter code and instructions for the analysis. I want you to try out both case deletion techniques (listwise and pairwise) and multiple imputation and compare the results across different these approaches to see how they compare. Report the model results using the [`modelsummary`](https://modelsummary.com/vignettes/modelsummary.html) command, and describe the results in the text.

When you are satisfied with your report, you should render it to PDF and submit the PDF on Canvas.
