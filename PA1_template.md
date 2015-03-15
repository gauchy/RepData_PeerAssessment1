# Reproducible Research: Peer Assessment 1


## Loading and preprocessing the data

```r
library(ggplot2)
library(lubridate)
rawdata <- read.csv("activity.csv");
rawdata$date <- ymd(rawdata$date)
completedata <- rawdata[complete.cases(rawdata),]
```


## What is mean total number of steps taken per day?

```r
totalStepsPerDay <- aggregate(steps~date,completedata,sum)
totalDays = dim(totalStepsPerDay)[[1]]
hist(totalStepsPerDay$steps,breaks=totalDays,main="Histogram of steps per day",col="red",xlab="Days",ylab="Steps")
```

![](PA1_template_files/figure-html/unnamed-chunk-2-1.png) 

```r
##Mean and median per day
```


## What is the average daily activity pattern?



## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
