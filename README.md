### Datafest-2018

# Mission Statement
We want to use unsupervised learning methods such as **K-means clustering** to see if anything naturally groups in normTitleCategory. We will aggregate the data by first grouping by jobIds since there are multiple job listings. We want every row to be one *UNIQUE* job.  


We initially drew a random sample of 500,000 observations. We made some variables modifications and pre-processed the data.

# Variable Assumptions
**jobId**
We will use the most recent date of a job posting, since there are multiple job listings with the same jobId.

**Word Count & Character length** 
Outliers will be assigned the median value in each variable.

**numReviews**
If a value is below the mean in numReviews, it is assigned to dummy variable: *few*. 
If above the mean, it is assigned to dummy variable: *many*. 
If the value is 0, then *both dummy variables are 0.*

**Date variable:**
We filtered the data from October 1st, 2016 to September 30th, 2017. We changed October 2016 dates to -1 and November 2016 dates to 0. We will use the latest date of the job posting (max). We plan to assign certain weights when we cluster. 
We divided the year into 4 seasons (binary variables: 0 or 1):

For **fall**:
* October
* November
* December 

For **winter**: (iswinter)
* January
* February
* March

For **spring**: (
* April
* May
* June 

For **summer**:
* July
* August
* September

**normSalary**
We normalized the estimateSalary by dividing salary by its corresponding *State's Per Capita Personal Income.* We also removed NA values in the estimateSalary.

**Country**
We filtered out Canada and Germany, and kept the US data.

**normTitleCategory**
For blank and uncategorized groups, we used dummy variables. We then grouped these categories into 5 broad categories:
* Medicine
* Technology
* Business
* Service
* Blue-collar

**jobAgeDays**
We will use the median value of jobAgeDays for the same job listings.

**clicks**
We will sum all of the clicks from all of the same job listings. It is a highly skewed right variable.

**clicksPerDay**
A new variable we created by dividing clicks.y by its corresponding day. We normalized *clicksPerDay* by using the *fourth root*, since it was the most skewed-right variable we had.

**Supervising & License**
We changed the NA values to 0.

## Aggregating the Data
We need to normalize every numeric variable by using the scale function, except for our binary variables. We normalized descriptionCharacterLength and description WordCount, clickPerDay, normSalary.

# R libraries used
* dplyr
* tidyverse
* ggplot2

## Machine Learning Methods
* K-means Clustering -- The Elbow Method
  -We clustered with characterlength, word count, is many, normsalary, iswinter, isspring, issummer, clicks per day.
  -stateprovince, country, city, normtitlecategory, educationrequirement, companyId.
