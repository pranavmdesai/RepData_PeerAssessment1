# Reproducible Research: Peer Assessment 1

## Loading and preprocessing the data

```r
library(data.table)
```

```
## Warning: package 'data.table' was built under R version 3.1.2
```

```r
library(reshape2)
activity <- read.csv("activity.csv", header = T)
activity <- data.table(activity)
```


## What is mean total number of steps taken per day?

```
##        steps       date interval totalperday
##     1:    NA 2012-10-01        0          NA
##     2:    NA 2012-10-01        5          NA
##     3:    NA 2012-10-01       10          NA
##     4:    NA 2012-10-01       15          NA
##     5:    NA 2012-10-01       20          NA
##    ---                                      
## 17564:    NA 2012-11-30     2335          NA
## 17565:    NA 2012-11-30     2340          NA
## 17566:    NA 2012-11-30     2345          NA
## 17567:    NA 2012-11-30     2350          NA
## 17568:    NA 2012-11-30     2355          NA
```

![](PA1_template_files/figure-html/extracting total activity per day-1.png) 



## What is the average daily activity pattern?

```r
melted <- melt(activity, id.vars = "interval", measure.vars="steps", value.name = "steps", na.rm = T)
average_daily_activity <- dcast(melted,interval~variable, mean)
```

```
## Using steps as value column: use value.var to override.
```

```r
plot(type="l",y=average_daily_activity$steps, x=average_daily_activity$interval, xlab="5 min interval", ylab="Average Steps Taken")
```

![](PA1_template_files/figure-html/calculating average steps per day-1.png) 

```r
average_daily_activity[which.max(average_daily_activity$steps),]
```

```
##     interval    steps
## 104      835 206.1698
```

```r
## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
```
