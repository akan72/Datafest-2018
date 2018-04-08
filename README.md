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

**Date:**
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

For **spring**: (isSpring)
* April
* May
* June 

For **summer**: (isSummer)
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

#Clustering
We clustered with characterlength, word count, isMany, normsalary, iswinter, isspring, issummer, clicksPerDay. After performing the elbow method to determine an optimal (k) number of clusters, k=5 was found to be optimal.

# Initial analysis:
We also computed relative proportions for each industry.

Cluster 1:
* **Characterlength and wordcount** seemed to be the most important -  more service industry versus tech. However, there is nothing super significant
* Most common industries: 
  1. sales
  2. retail
  3. service
* Least common industries: 
  1. techsoftware
  2. meddental
  3. meddr

Cluster 2:
* **Salary** seemed to be the most important - high-skilled jobs 
* Most 5 common industries: 
  1. accounting
  2. architecture
  3. engineering(engchem, engelectric, engid, engmech)
  4. finance
  5. install
  6. meddr
  7. project
  8. techsoftware
* Least 5 common industry: 
  1. childcare
  2. food
  3. personal
  4. retail
  5. warehouse

Cluster 3
* **Low** characterlengths and wordcount
* Most 5 common industries: 
  1. veterinary
  2. sanitation
  3. driver
  4. personal
  5. science
  6. warehouse
* Low 5 common industries:
  1. finance
  2. marketing
  3. military
  4. socialscience
  5. transport

Cluster 4:
* not useful -- *average*
* Most common industries:
  1. admin
  2. agriculture
  3. care
  4. customer
  5. hospitality
  6. service
* Low common industries: 
1. childcare
2. engchem
3. engid
4. techinfo

Cluster 5:
* **clicks** seemed to be the most important
* Most 5 common industries: 
  1. accounting
  2. childcare
  3. customer
  4. driver
  5. service
  6. tech software
* Low 5 common industries: 
  1. aviation
  2. agriculture
  3. engchem
  4. mining
  5. military

We created proportions of each category in normTitleCategory for each cluster and created a new dataframe to compare each clusters.

## Plotting
Important Variables used as the axes:
*Salary, Wordsmean, ClicksPerDay

