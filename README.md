# Modeling 2016 Election Results
## Introduction
I set out to build a Linear Regression model to identify the relative importance of county level demographic features in determining the proportion of that county that voted for Donald Trump in the 2016 presidential election.  I obtained my feature data from the US Census website in Excel format and merged this with 2016 county level election results from Harvard Dataverse.  My best performing model used Lasso Feature Selection and had a Testing RMSE of .092.  The two features that most positively predicted support for Donald Trump were Caucasian Population proportion and Veteran proportion, while the two features that most negatively influenced support for Donald Trump were Bachelors Degree Population proportion and Hispanic Population proportion.

## Obtain Data
I obtained county level data in excel format for 33 demographic features from the US Census website.  Data was abailable for the 785 largest counties in the US accounting for approximately 85% of the national population.  I also downloaded an Excel file with 2016 county level presidential election results from Harvard Dataverse.  I merged the county level demographics Excel files with the election results Excel file, yielding 785 datapoints.  

## Scrub Data
The first issues I faced while scrubbing my data was the presense of two county level equivalents in Virginia, counties and independent cities, which sometimes had duplicate names.  I identified duplicate county names and manually updated those names to specify whether they were counties or independent cities.  I replaced missing feature values with the mean for those features.  I also applied a standard scaler to my features, in order to make the relative importance of coefficients in my linear regression model comparable.  Finally, I created interactions to have more features to include in my model.

## Explore Data
In the process of performing EDA, I discovered that many features had non-linear relationships with proportion of support for Donald Trump.  I used log transformations to update features with non-linear relationships to have linear relationships with the dependent variable.  I also created a correlation matrix of my independent variables and removed heavily correlated ones.

## Model Data
I used RMSE as my principle evaluation metric in order to measure the difference between my model predictions and the actual values, while disproportionately punishing large prediction misses. I used an 80/20 Train Test Split to validate my model.  Using Lasso feature selection, my testing RMSE was .092.  The most important features in increasing support for Donald Trump were Caucasian Population proportion, Veteran Population proportion and Mining Jobs per Capita with coefficients of .05, .03 and .02 respectively.  The most influential features in decreasing support for Donald Trump were population proportion with a Bachelors Degree, Hispanic Population proportion and Population Density with coefficients of -.04, -.02 and -.01 respectively.

## Next steps
With more time, I would like to train additional types of regression models to see if they could outperform linear regression in RMSE.  I would also like to use more recent census demographic data to predict how demographic changes from 2016 to 2020 might impact the 2020 presidential election.

# Github Files
[Mod_2_Final.ipynb](https://github.com/blantj/Mod_2_Project/blob/master/Mod_2_Final.ipynb) :  2016 election results regression modeling

# Sources
US Census Data: https://www.census.gov/data.html

Election Results: https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/VOQCHQ
