# Reproducible Research: Peer Assessment 1
Joshua Poirier

## Loading and preprocessing the data
If it hasn't been unzipped, unzip the *activity.zip* file from the present working directory:

```r
if (!file.exists("activity.csv")) {
    unzip("activity.zip")
}
```

Load the data into a data frame called *data*:

```r
data <- read.csv("activity.csv", header=TRUE, nrows=17568)
summary(data)
```

```
##      steps               date          interval   
##  Min.   :  0.0   2012-10-01:  288   Min.   :   0  
##  1st Qu.:  0.0   2012-10-02:  288   1st Qu.: 589  
##  Median :  0.0   2012-10-03:  288   Median :1178  
##  Mean   : 37.4   2012-10-04:  288   Mean   :1178  
##  3rd Qu.: 12.0   2012-10-05:  288   3rd Qu.:1766  
##  Max.   :806.0   2012-10-06:  288   Max.   :2355  
##  NA's   :2304    (Other)   :15840
```


## What is mean total number of steps taken per day?



## What is the average daily activity pattern?



## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
