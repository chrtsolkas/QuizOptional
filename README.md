# Optional Quiz
This repo contains the RDS file for the optional practice at the end of week 3 of the Regression Models course in Coursera Data Science Specialization.

## Objective
Our objective is to study how income varies across different categories of college majors. We will be using data from a study of recent college graduates. 
Specifically answer: “Is there an association between college major category and income?”

## Answer
We first conduct an exploratory analysis of the dataset.

Dims: 173 observations of 19 variables

Unique major categories: 16

There are some NAs (NaNs) present in columns perc_employed_parttime, perc_college_jobs, perc_non_college_jobs and perc_low_wage_jobs (1 NA per column, 2 cases).

Then we make box plots for the median income per major category. We observe that the median income per category lays between 33500 and 40000. The exceptions are Communications & Journalism and Physical Sciences with higher values and Interdisciplinary with the lower value of 27500. So the medians are relatively close to each other.

Next we make a scatter plot with the major categories versus mean income per category and we observe that Business has a high mean (mostly because of an outlier at rank 63). This category has the most samples (15505). The graph demonstrates a trend between categories but we must be really careful of the interpretation since we aggregate the data. There moght be a case of Simpson's Paradox.

Next we do a correlogram to find out about posible correlations in the variables. There are no surprises here: There are strong correlations among perc_men and perc_women, perc_employed and perc_unemployed, perc_employed_parttime and perc_employed_fulltime, perc_college_jobs and perc_non_college_jobs (and a smaller correlation of this two with perc_low_wage_jobs) and finally a strong corellation among p25th, median and p75th. So if we include some variable to our model we should not include in our model the variables that are highly correlated to the one we used.

We next start fitting linear models to the dataset. We observe that when fitting lm(formula = median ~ major_category, data = college) there is no significant difference in the means of the median income for each major category and thus we conclude that previously we witnessed the Simpson's Paradox when we aggregated the dataset.

Looking for confound variables we add the gender (perc_women or perc_men) and we find that there is no significant change in our fitted model. We also try to fit other variables like perc_employed and perc_college_jobs but we observed no significant changes to our model.

Finally from the plots of the fitted model lm(formula = median ~ major_category, data = college) we see that there are no systematic changes to residuals and the outliers do not have significant influence in our model.

So we conclude that there is no association between college major category and income.
