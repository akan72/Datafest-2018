## Datafest-2018

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
We normalized the estimateSalary by dividing salary by each *State's Per Capita Personal Income.*
