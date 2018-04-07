## Datafest-2018

# Mission Statement
We want to use K-means clustering (unsupervised learning) to see if anything cool happens.

We initially drew a random sample of 1,000,000 observations. We made some variables modifications and pre-processing the data.

# Variable Assumptions
**Word Count & Character length** 
Outliers will be assigned the median value in each variable.

**numReviews**
If a value is below the mean in numReviews, it is assigned to dummy variable: few. 
If above the mean, it is assigned to dummy variable: many. 
If the value is 0, then both dummy variables are 0.

**Date variable:**
We filtered the data from October 1st, 2016 to September 30th, 2017. 
We divided the year into 4 seasons:

For fall:
* October
* November
* December 

For winter:
* January
* February
* March

For spring:
* April
* May
* June 

For summer:
* July
* August
* September

**estimateSalary**
We normalized the estimateSalary by dividing salary by its corresponding *State's Per Capita Personal Income.* We also removed NA values in the estimateSalary.

**Country**
We filtered out Canada and Germany.

**normTitleCategory**
For blank and uncategorized groups, we used dummy variables. We then grouped these categories into 5 broad categories:
* Medicine
* Technology
* Business
* Service
* Blue-collar

**avglocalclick**
We changed 0 values in jobAgeDay to 1. We are dividing the localclick by jobAgeDays.

**Supervising & License**
We changed the NA values to 0.

