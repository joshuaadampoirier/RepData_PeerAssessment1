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
data <- read.csv("activity.csv", header=TRUE, nrows=17568, stringsAsFactors=FALSE)
```

Pre-process the data by formatting the *date* as a date object:

```r
library(lubridate)
data$date <- ymd(data$date)
#data$time <- formatC(data$interval, width=4, format="d", flag="0")
#data$time <- paste0(substr(data$time,1,2), ":", substr(data$time,3,4))
#data$time <- hm(data$time)
```

Show some data!

```
##       steps       date interval
## 17566    NA 2012-11-30     2345
## 17567    NA 2012-11-30     2350
## 17568    NA 2012-11-30     2355
```

## What is mean total number of steps taken per day?
Build a new data frame from *data* that calculates the total number of steps taken on each day:

```r
dailySteps <- aggregate(x=data$steps, by=list(data$date), FUN=sum, na.rm=TRUE)
names(dailySteps) <- c("Date", "TotalSteps")
meanTotalSteps <- mean(dailySteps$TotalSteps)
head(dailySteps,3)
```

```
##         Date TotalSteps
## 1 2012-10-01          0
## 2 2012-10-02        126
## 3 2012-10-03      11352
```

The mean total number of steps taken per day is **9354**.  We show zero decimal places here as the raw data has zero decimal places, meaning zero significant digits!



## What is the average daily activity pattern?
Build a new data frame from *data* that calculates the average daily activity pattern:

```r
dailyActivity <- aggregate(x=data$steps, by=list(data$interval), FUN=mean, na.rm=TRUE)
names(dailyActivity) <- c("Interval", "MeanSteps")
head(dailyActivity,3)
```

```
##   Interval MeanSteps
## 1        0    1.7170
## 2        5    0.3396
## 3       10    0.1321
```

Let's create a time series plot of the mean steps:
![plot of chunk unnamed-chunk-6](./PA1_template_files/figure-html/unnamed-chunk-6.png) 

## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
