### Datafest-2018

# Mission Statement
We want to use unsupervised learning methods such as **K-means clustering and Principal Component Analysis (PCA)** to see if anything cool happens. We want to use PCA first to reduce the dimensions and then use K-means clustering. We will aggregate the data by first grouping by jobIds since there are multiple job listings. We want every row to be one *UNIQUE* job.  


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

For **winter**:
* January
* February
* March

For **spring**:
* April
* May
* June 

For **summer**:
* July
* August
* September

**estimateSalary**
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
We will sum all of the clicks from all of the same job listings.

**Supervising & License**
We changed the NA values to 0.

## Aggregating the Data
We need to normalize every numeric variable. We normalized *clicks* by using cubed root, since it was the most skewed-right variable we had. For the remaining numeric variables, we used ______ some function add here pls, except for the binary variables.

## Machine Learning Methods
* K-means Clustering -- The Elbow Method
* Principal Component Analysis
