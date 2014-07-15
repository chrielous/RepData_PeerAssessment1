# Reproducible Research: Peer Assessment 1

# Activity Monitoring Data Analysis
========================================================

## Loading and preprocessing the data

### Load activity.csv file into dataframe filedata, and create stesdate dataframe with date and total number of steps on each day.


```r
filedata<-read.csv("activity.csv")
stepsdate<-tapply(filedata$steps,filedata$date,sum)
```

## What is mean total number of steps taken per day?

### Histogram showing the total number of steps taken each day versus date:


```r
hist(stepsdate,xlab="total steps per day",ylab="number of days",main="histogram of daily steps")
```

![plot of chunk unnamed-chunk-2](figure/unnamed-chunk-2.png) 

### Find mean step per day by applying mean function to steps on each date:

```r
meansteps<-aggregate(filedata$steps,by=list(filedata$date),FUN=mean)
names(meansteps)<-c("date","meanstep")
kable(meansteps)
```

```
## 
## 
## |date       | meanstep|
## |:----------|--------:|
## |2012-10-01 |       NA|
## |2012-10-02 |   0.4375|
## |2012-10-03 |  39.4167|
## |2012-10-04 |  42.0694|
## |2012-10-05 |  46.1597|
## |2012-10-06 |  53.5417|
## |2012-10-07 |  38.2465|
## |2012-10-08 |       NA|
## |2012-10-09 |  44.4826|
## |2012-10-10 |  34.3750|
## |2012-10-11 |  35.7778|
## |2012-10-12 |  60.3542|
## |2012-10-13 |  43.1458|
## |2012-10-14 |  52.4236|
## |2012-10-15 |  35.2049|
## |2012-10-16 |  52.3750|
## |2012-10-17 |  46.7083|
## |2012-10-18 |  34.9167|
## |2012-10-19 |  41.0729|
## |2012-10-20 |  36.0938|
## |2012-10-21 |  30.6285|
## |2012-10-22 |  46.7361|
## |2012-10-23 |  30.9653|
## |2012-10-24 |  29.0104|
## |2012-10-25 |   8.6528|
## |2012-10-26 |  23.5347|
## |2012-10-27 |  35.1354|
## |2012-10-28 |  39.7847|
## |2012-10-29 |  17.4236|
## |2012-10-30 |  34.0938|
## |2012-10-31 |  53.5208|
## |2012-11-01 |       NA|
## |2012-11-02 |  36.8056|
## |2012-11-03 |  36.7049|
## |2012-11-04 |       NA|
## |2012-11-05 |  36.2465|
## |2012-11-06 |  28.9375|
## |2012-11-07 |  44.7326|
## |2012-11-08 |  11.1771|
## |2012-11-09 |       NA|
## |2012-11-10 |       NA|
## |2012-11-11 |  43.7778|
## |2012-11-12 |  37.3785|
## |2012-11-13 |  25.4722|
## |2012-11-14 |       NA|
## |2012-11-15 |   0.1424|
## |2012-11-16 |  18.8924|
## |2012-11-17 |  49.7882|
## |2012-11-18 |  52.4653|
## |2012-11-19 |  30.6979|
## |2012-11-20 |  15.5278|
## |2012-11-21 |  44.3993|
## |2012-11-22 |  70.9271|
## |2012-11-23 |  73.5903|
## |2012-11-24 |  50.2708|
## |2012-11-25 |  41.0903|
## |2012-11-26 |  38.7569|
## |2012-11-27 |  47.3819|
## |2012-11-28 |  35.3576|
## |2012-11-29 |  24.4688|
## |2012-11-30 |       NA|
```

### Find median step per day by applying median function to stpes on each date, with not valid number ignored:

```r
filedatawona<-subset(filedata,!is.na(filedata$steps))
mediansteps<-aggregate(filedatawona$steps,by=list(filedatawona$date),FUN=median)
names(mediansteps)<-c("date","median")
kable(mediansteps)
```

```
## 
## 
## |date       | median|
## |:----------|------:|
## |2012-10-02 |      0|
## |2012-10-03 |      0|
## |2012-10-04 |      0|
## |2012-10-05 |      0|
## |2012-10-06 |      0|
## |2012-10-07 |      0|
## |2012-10-09 |      0|
## |2012-10-10 |      0|
## |2012-10-11 |      0|
## |2012-10-12 |      0|
## |2012-10-13 |      0|
## |2012-10-14 |      0|
## |2012-10-15 |      0|
## |2012-10-16 |      0|
## |2012-10-17 |      0|
## |2012-10-18 |      0|
## |2012-10-19 |      0|
## |2012-10-20 |      0|
## |2012-10-21 |      0|
## |2012-10-22 |      0|
## |2012-10-23 |      0|
## |2012-10-24 |      0|
## |2012-10-25 |      0|
## |2012-10-26 |      0|
## |2012-10-27 |      0|
## |2012-10-28 |      0|
## |2012-10-29 |      0|
## |2012-10-30 |      0|
## |2012-10-31 |      0|
## |2012-11-02 |      0|
## |2012-11-03 |      0|
## |2012-11-05 |      0|
## |2012-11-06 |      0|
## |2012-11-07 |      0|
## |2012-11-08 |      0|
## |2012-11-11 |      0|
## |2012-11-12 |      0|
## |2012-11-13 |      0|
## |2012-11-15 |      0|
## |2012-11-16 |      0|
## |2012-11-17 |      0|
## |2012-11-18 |      0|
## |2012-11-19 |      0|
## |2012-11-20 |      0|
## |2012-11-21 |      0|
## |2012-11-22 |      0|
## |2012-11-23 |      0|
## |2012-11-24 |      0|
## |2012-11-25 |      0|
## |2012-11-26 |      0|
## |2012-11-27 |      0|
## |2012-11-28 |      0|
## |2012-11-29 |      0|
```

## What is the average daily activity pattern?

### Time series plot of the 5-minute interval (x-axis) and the average number of steps taken, averaged across all days (y-axis):

```r
stepsdata<-subset(filedata,!is.na(filedata$steps))
stepts<-aggregate(stepsdata$steps, by=list(stepsdata$interval), FUN=mean)
plot(stepts,type="l",xlab="Interval", ylab="Average Steps")
```

![plot of chunk unnamed-chunk-5](figure/unnamed-chunk-5.png) 



```r
names(stepts)<-c("interval","avgsteps")
maxstepinterval<-subset(stepts,stepts$avgsteps==max(stepts$avgsteps))$interval
```

### Interval 835 contains the maximum number of steps.

## Imputing missing values


```r
numofnas<-length(subset(filedata,is.na(filedata$steps))[,1])
```

### There are 2304 NAs on the file.

### Using the mean steps of corresponding 5-minute interval to fill in missing data:


```r
fulldata<-filedata
for(n in 1:length(fulldata[,1]))
{
    record<-fulldata[n,]
    if(is.na(record$steps))
    {
      interval<-record$interval
      meanstep<- stepts[stepts$interval==interval,]$avgsteps
      fulldata[n,]$steps = meanstep
    }
}

fullstepsdate<-tapply(fulldata$steps,fulldata$date,sum)
```

### Histogram of the total number of steps taken each day with missing value filled in:

```r
hist(fullstepsdate,xlab="total steps per day",ylab="number of days",main="histogram of daily steps")
```

![plot of chunk unnamed-chunk-9](figure/unnamed-chunk-9.png) 

### Find mean step per day by applying mean function to steps on each date with missing value filled in:

```r
fullmeansteps<-aggregate(fulldata$steps,by=list(fulldata$date),FUN=mean)
names(fullmeansteps)<-c("date","meanstep")
kable(fullmeansteps)
```

```
## 
## 
## |date       | meanstep|
## |:----------|--------:|
## |2012-10-01 |  37.3826|
## |2012-10-02 |   0.4375|
## |2012-10-03 |  39.4167|
## |2012-10-04 |  42.0694|
## |2012-10-05 |  46.1597|
## |2012-10-06 |  53.5417|
## |2012-10-07 |  38.2465|
## |2012-10-08 |  37.3826|
## |2012-10-09 |  44.4826|
## |2012-10-10 |  34.3750|
## |2012-10-11 |  35.7778|
## |2012-10-12 |  60.3542|
## |2012-10-13 |  43.1458|
## |2012-10-14 |  52.4236|
## |2012-10-15 |  35.2049|
## |2012-10-16 |  52.3750|
## |2012-10-17 |  46.7083|
## |2012-10-18 |  34.9167|
## |2012-10-19 |  41.0729|
## |2012-10-20 |  36.0938|
## |2012-10-21 |  30.6285|
## |2012-10-22 |  46.7361|
## |2012-10-23 |  30.9653|
## |2012-10-24 |  29.0104|
## |2012-10-25 |   8.6528|
## |2012-10-26 |  23.5347|
## |2012-10-27 |  35.1354|
## |2012-10-28 |  39.7847|
## |2012-10-29 |  17.4236|
## |2012-10-30 |  34.0938|
## |2012-10-31 |  53.5208|
## |2012-11-01 |  37.3826|
## |2012-11-02 |  36.8056|
## |2012-11-03 |  36.7049|
## |2012-11-04 |  37.3826|
## |2012-11-05 |  36.2465|
## |2012-11-06 |  28.9375|
## |2012-11-07 |  44.7326|
## |2012-11-08 |  11.1771|
## |2012-11-09 |  37.3826|
## |2012-11-10 |  37.3826|
## |2012-11-11 |  43.7778|
## |2012-11-12 |  37.3785|
## |2012-11-13 |  25.4722|
## |2012-11-14 |  37.3826|
## |2012-11-15 |   0.1424|
## |2012-11-16 |  18.8924|
## |2012-11-17 |  49.7882|
## |2012-11-18 |  52.4653|
## |2012-11-19 |  30.6979|
## |2012-11-20 |  15.5278|
## |2012-11-21 |  44.3993|
## |2012-11-22 |  70.9271|
## |2012-11-23 |  73.5903|
## |2012-11-24 |  50.2708|
## |2012-11-25 |  41.0903|
## |2012-11-26 |  38.7569|
## |2012-11-27 |  47.3819|
## |2012-11-28 |  35.3576|
## |2012-11-29 |  24.4688|
## |2012-11-30 |  37.3826|
```

### Find median step per day by applying median function to stpes on each date with missing value filled in:

```r
mediansteps<-aggregate(fulldata$steps,by=list(fulldata$date),FUN=median)
names(mediansteps)<-c("date","median")
kable(mediansteps)
```

```
## 
## 
## |date       | median|
## |:----------|------:|
## |2012-10-01 |  34.11|
## |2012-10-02 |   0.00|
## |2012-10-03 |   0.00|
## |2012-10-04 |   0.00|
## |2012-10-05 |   0.00|
## |2012-10-06 |   0.00|
## |2012-10-07 |   0.00|
## |2012-10-08 |  34.11|
## |2012-10-09 |   0.00|
## |2012-10-10 |   0.00|
## |2012-10-11 |   0.00|
## |2012-10-12 |   0.00|
## |2012-10-13 |   0.00|
## |2012-10-14 |   0.00|
## |2012-10-15 |   0.00|
## |2012-10-16 |   0.00|
## |2012-10-17 |   0.00|
## |2012-10-18 |   0.00|
## |2012-10-19 |   0.00|
## |2012-10-20 |   0.00|
## |2012-10-21 |   0.00|
## |2012-10-22 |   0.00|
## |2012-10-23 |   0.00|
## |2012-10-24 |   0.00|
## |2012-10-25 |   0.00|
## |2012-10-26 |   0.00|
## |2012-10-27 |   0.00|
## |2012-10-28 |   0.00|
## |2012-10-29 |   0.00|
## |2012-10-30 |   0.00|
## |2012-10-31 |   0.00|
## |2012-11-01 |  34.11|
## |2012-11-02 |   0.00|
## |2012-11-03 |   0.00|
## |2012-11-04 |  34.11|
## |2012-11-05 |   0.00|
## |2012-11-06 |   0.00|
## |2012-11-07 |   0.00|
## |2012-11-08 |   0.00|
## |2012-11-09 |  34.11|
## |2012-11-10 |  34.11|
## |2012-11-11 |   0.00|
## |2012-11-12 |   0.00|
## |2012-11-13 |   0.00|
## |2012-11-14 |  34.11|
## |2012-11-15 |   0.00|
## |2012-11-16 |   0.00|
## |2012-11-17 |   0.00|
## |2012-11-18 |   0.00|
## |2012-11-19 |   0.00|
## |2012-11-20 |   0.00|
## |2012-11-21 |   0.00|
## |2012-11-22 |   0.00|
## |2012-11-23 |   0.00|
## |2012-11-24 |   0.00|
## |2012-11-25 |   0.00|
## |2012-11-26 |   0.00|
## |2012-11-27 |   0.00|
## |2012-11-28 |   0.00|
## |2012-11-29 |   0.00|
## |2012-11-30 |  34.11|
```

## Are there differences in activity patterns between weekdays and weekends?

### plot of the daily patterns for weekdays and weekends:

```r
days<-character()
for(n in 1:length(fulldata[,1]))
{
   dt<-fulldata[n,]$date
   dt<-as.Date(dt,"%Y-%m-%d")
   if(weekdays(dt) %in% c("Sunday","Saturday"))
     days<-c(days,"weekend")
   else
     days<-c(days,"weekday")
}
days<-factor(days)
datawday<-cbind(fulldata,days) 

dataweekday<-subset(datawday,datawday$days=="weekday")
dataweekend<-subset(datawday,datawday$days=="weekend")

stepwdts<-aggregate(dataweekday$steps, by=list(dataweekday$interval), FUN=mean)
names(stepwdts)<-c("interval","avg. steps")

stepwendts<-aggregate(dataweekend$steps, by=list(dataweekend$interval), FUN=mean)
names(stepwendts)<-c("interval","avg. steps")

par(mfrow=c(2,1))
plot(stepwdts,type="l",xlab="Interval", ylab="Average Steps",main="weekdays")
plot(stepwendts,type="l",xlab="Interval", ylab="Average Steps",main="weekends")
```

![plot of chunk unnamed-chunk-12](figure/unnamed-chunk-12.png) 

### Above panel plot shows differences between weekday activities and weekend activities. People are more active in the morning on weekdays, and on weekends their activities are likely in the afternoon.
