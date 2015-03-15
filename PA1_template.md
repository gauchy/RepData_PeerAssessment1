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
meansteps <- mean(totalStepsPerDay$steps)
mediansteps <- median(totalStepsPerDay$steps)
```
mean of total steps per day  1.0766189\times 10^{4}  
median of total steps per day  10765


## What is the average daily activity pattern?

```r
intervalBasedAvg <- aggregate(steps~interval,completedata,mean)
g <- ggplot(intervalBasedAvg,aes(x=interval,y=steps)) + geom_line();
g <- g + labs(x="interval",y="average steps")
g <- g + ggtitle("Average steps over intervals")
print(g)
```

![](PA1_template_files/figure-html/unnamed-chunk-3-1.png) 

```r
maxAvg <- max(intervalBasedAvg$steps)
```
The maximum average over intervals is 206.1698113

## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
