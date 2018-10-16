The reproducible research assignmnent
=====================================
Read to object mydata and format the dates


    

```r
mydata <- read.csv("activity.csv", sep=",")
mydata$date <- as.Date(mydata$date, format="%m/%d/%Y")
```

The total number of steps taken per day


```r
sumstepsbyday <- by(mydata[, 1], mydata$date, sum, na.rm=TRUE)
sumstepsbyday
```

```
## mydata$date: 2012-10-01
## [1] 0
## -------------------------------------------------------- 
## mydata$date: 2012-10-02
## [1] 126
## -------------------------------------------------------- 
## mydata$date: 2012-10-03
## [1] 11352
## -------------------------------------------------------- 
## mydata$date: 2012-10-04
## [1] 12116
## -------------------------------------------------------- 
## mydata$date: 2012-10-05
## [1] 13294
## -------------------------------------------------------- 
## mydata$date: 2012-10-06
## [1] 15420
## -------------------------------------------------------- 
## mydata$date: 2012-10-07
## [1] 11015
## -------------------------------------------------------- 
## mydata$date: 2012-10-08
## [1] 0
## -------------------------------------------------------- 
## mydata$date: 2012-10-09
## [1] 12811
## -------------------------------------------------------- 
## mydata$date: 2012-10-10
## [1] 9900
## -------------------------------------------------------- 
## mydata$date: 2012-10-11
## [1] 10304
## -------------------------------------------------------- 
## mydata$date: 2012-10-12
## [1] 17382
## -------------------------------------------------------- 
## mydata$date: 2012-10-13
## [1] 12426
## -------------------------------------------------------- 
## mydata$date: 2012-10-14
## [1] 15098
## -------------------------------------------------------- 
## mydata$date: 2012-10-15
## [1] 10139
## -------------------------------------------------------- 
## mydata$date: 2012-10-16
## [1] 15084
## -------------------------------------------------------- 
## mydata$date: 2012-10-17
## [1] 13452
## -------------------------------------------------------- 
## mydata$date: 2012-10-18
## [1] 10056
## -------------------------------------------------------- 
## mydata$date: 2012-10-19
## [1] 11829
## -------------------------------------------------------- 
## mydata$date: 2012-10-20
## [1] 10395
## -------------------------------------------------------- 
## mydata$date: 2012-10-21
## [1] 8821
## -------------------------------------------------------- 
## mydata$date: 2012-10-22
## [1] 13460
## -------------------------------------------------------- 
## mydata$date: 2012-10-23
## [1] 8918
## -------------------------------------------------------- 
## mydata$date: 2012-10-24
## [1] 8355
## -------------------------------------------------------- 
## mydata$date: 2012-10-25
## [1] 2492
## -------------------------------------------------------- 
## mydata$date: 2012-10-26
## [1] 6778
## -------------------------------------------------------- 
## mydata$date: 2012-10-27
## [1] 10119
## -------------------------------------------------------- 
## mydata$date: 2012-10-28
## [1] 11458
## -------------------------------------------------------- 
## mydata$date: 2012-10-29
## [1] 5018
## -------------------------------------------------------- 
## mydata$date: 2012-10-30
## [1] 9819
## -------------------------------------------------------- 
## mydata$date: 2012-10-31
## [1] 15414
## -------------------------------------------------------- 
## mydata$date: 2012-11-01
## [1] 0
## -------------------------------------------------------- 
## mydata$date: 2012-11-02
## [1] 10600
## -------------------------------------------------------- 
## mydata$date: 2012-11-03
## [1] 10571
## -------------------------------------------------------- 
## mydata$date: 2012-11-04
## [1] 0
## -------------------------------------------------------- 
## mydata$date: 2012-11-05
## [1] 10439
## -------------------------------------------------------- 
## mydata$date: 2012-11-06
## [1] 8334
## -------------------------------------------------------- 
## mydata$date: 2012-11-07
## [1] 12883
## -------------------------------------------------------- 
## mydata$date: 2012-11-08
## [1] 3219
## -------------------------------------------------------- 
## mydata$date: 2012-11-09
## [1] 0
## -------------------------------------------------------- 
## mydata$date: 2012-11-10
## [1] 0
## -------------------------------------------------------- 
## mydata$date: 2012-11-11
## [1] 12608
## -------------------------------------------------------- 
## mydata$date: 2012-11-12
## [1] 10765
## -------------------------------------------------------- 
## mydata$date: 2012-11-13
## [1] 7336
## -------------------------------------------------------- 
## mydata$date: 2012-11-14
## [1] 0
## -------------------------------------------------------- 
## mydata$date: 2012-11-15
## [1] 41
## -------------------------------------------------------- 
## mydata$date: 2012-11-16
## [1] 5441
## -------------------------------------------------------- 
## mydata$date: 2012-11-17
## [1] 14339
## -------------------------------------------------------- 
## mydata$date: 2012-11-18
## [1] 15110
## -------------------------------------------------------- 
## mydata$date: 2012-11-19
## [1] 8841
## -------------------------------------------------------- 
## mydata$date: 2012-11-20
## [1] 4472
## -------------------------------------------------------- 
## mydata$date: 2012-11-21
## [1] 12787
## -------------------------------------------------------- 
## mydata$date: 2012-11-22
## [1] 20427
## -------------------------------------------------------- 
## mydata$date: 2012-11-23
## [1] 21194
## -------------------------------------------------------- 
## mydata$date: 2012-11-24
## [1] 14478
## -------------------------------------------------------- 
## mydata$date: 2012-11-25
## [1] 11834
## -------------------------------------------------------- 
## mydata$date: 2012-11-26
## [1] 11162
## -------------------------------------------------------- 
## mydata$date: 2012-11-27
## [1] 13646
## -------------------------------------------------------- 
## mydata$date: 2012-11-28
## [1] 10183
## -------------------------------------------------------- 
## mydata$date: 2012-11-29
## [1] 7047
## -------------------------------------------------------- 
## mydata$date: 2012-11-30
## [1] 0
```

Histogram of the number of steps taken each day


```r
hist(sumstepsbyday, main ="Total number of steps taken each day", xlab="Number of steps", ylab="Frequency", breaks=10)
```

![plot of chunk P1](instructions_fig/P1-1.png)

The mean and median of total number of steps taken each day


```r
sumstepbyday1 <- by(mydata[, 1], mydata$date, sum)
meanstepsbyday <- mean(sumstepbyday1, na.rm=TRUE)
meanstepsbyday 
```

```
## [1] 10766.19
```

```r
medianstepsbyday <- median(sumstepbyday1, na.rm=TRUE)
medianstepsbyday
```

```
## [1] 10765
```

Calculate and plot the average daily activity pattern


```r
avgsteachintv <- by(mydata[, 1], mydata$interval, mean, na.rm=TRUE)
mydata$interval <- as.factor(mydata$interval)
```

```r
plot(levels(mydata$interval), avgsteachintv,type="l", xlab="time interval", ylab="average no of steps each inverval")
```

![plot of chunk P2](instructions_fig/P2-1.png)

Determine the 5-minute interval, on average across all the days in the dataset, contains the maximum number of steps


```r
maxsteps <- max(avgsteachintv)
x <- levels(mydata$interval)
x[which(avgsteachintv == maxsteps)]
```

```
## [1] "835"
```

Calculate and report the total number of missing values, i.e., NAs


```r
sum(is.na(mydata))
```

```
## [1] 2304
```


Imputing the missing values
we impute missing values using the mean of the number of steps for that day
use the packages Hmisc


calculate the avg number of steps each day


```r
library(Hmisc)
meanstepseachday <- by(mydata[, 1], mydata$date, mean)
```

Create a vector where to copy imputed values


```r
d.impvalues <- vector(mode="double", length=nrow(meanstepseachday))
```

There are some days where no steps are taken. We use zero steps for those days for all the not available data


```r
i <- 1
for (i in 1:nrow(meanstepseachday)) {
	if(is.na(meanstepseachday[i])==F) {
		d.impvalues[i] <- meanstepseachday[i] 
		}
	else {
		d.impvalues[i] <- 0
		}
}
```

Create a vector to store all imputable values across all steps in case they are missing (NA)


```r
m.impvalues <- vector(mode="double", length=nrow(mydata))
```

Copy the values for each day across all records of steps taken
we first determine the unique number of dates and time interval in the data set


```r
mydata$date <- as.factor(mydata$date)
uniquedates <- length(levels(mydata$date))

uniqueintv <- length(levels(mydata$interval))
```

Copy vales for each day across all records of steps taken


```r
j <- 1
k <- 1
kk <- 1
for (j in 1:uniquedates) {
	for (k in 1:uniqueintv) {
		m.impvalues[kk] <- d.impvalues[j]
		kk <- kk+1
	}
 }
```

Through the original dataset, look for missing values and substitute with the mean for that day. These are contained in the vector [m.impvalues]


```r
jj <- 1
for (jj in 1:nrow(mydata)) {
	if (is.na(mydata$steps[jj])==T) {
		mydata$steps[jj] <- m.impvalues[jj]
		}
}
```

The dataset is now without missing values and we can call it: mynewdata. Check out the top ten observations of the new dataset


```r
mynewdata <- mydata
```

Check if the new dataset has any missing observations


```r
sum(is.na(mynewdata))
```

```
## [1] 0
```

Histogram of the total number of steps taken each day and Calculate and report the mean and median total number of steps taken per day



```r
sumsteps <- by(mynewdata[, 1], mynewdata$date, sum, na.rm=TRUE)
```

```r
hist(sumsteps, main ="Total number of steps taken each day", xlab="Number of steps", ylab="Frequency", breaks=10)
```

![plot of chunk P3](instructions_fig/P3-1.png)

New values of mean and median


```r
mean(sumsteps)
```

```
## [1] 9354.23
```

```r
median(sumsteps)
```

```
## [1] 10395
```

Old values of mean and median


```r
meanstepsbyday
```

```
## [1] 10766.19
```

```r
medianstepsbyday
```

```
## [1] 10765
```

The resuls above show that there is a difference between the mean and median because the imputed values are zero in all cases since for any missing data, it is missing all day and have been substitued for zero. This lowers the mean and median, If a different value, say, for the preceeding or proceeding day had been used, the values would have been higher


Create a new variable. Let us call it : wday
Then determine the day of the week for 
first store in a vector: dayofweek and copy it in
each entry and fill it in the newly created column


```r
mynewdata[,4] <- NA
names(mynewdata) <- c("steps", "date", "interval", "wday")

dayofweek <- weekdays(as.POSIXct(mynewdata$date), abbreviate = TRUE)

ii <- 1
for (ii in 1:nrow(mynewdata)) {
	if (dayofweek [ii] == "Sat") {
		mynewdata$wday[ii] <- "weekend"
	}else if (dayofweek [ii] == "Sun") {
		mynewdata$wday[ii] <- "weekend"
	}else {
		mynewdata$wday[ii] <- "weekday"
	}
}
```


Make a panel plot containing a time series plot (i.e. type="l") of the 5-minute interval (x-axis) and the average number of steps taken, averaged across all weekday days or weekend days (y-axis). 
first subset the data and average the steps for weekdays and weekend


```r
wdaydata <- subset(mynewdata, wday == "weekday")
weekenddata <- subset(mynewdata, wday == "weekend")
```

Determine the mean for each and make a plot. 


```r
wdaysteps <- by(wdaydata[, 1], wdaydata$interval, mean)
weekendsteps <- by(weekenddata[, 1], weekenddata$interval, mean)
```

Plotting the average number of steps each day for weekdays and weekends for each time interval. The base plot is good enough as per instructions


```r
mynewdata$interval <- as.factor(mynewdata$interval)
```

```r
par(mfrow=c(2,1))
plot(levels(mynewdata$interval), weekendsteps, type="l", xlab="interval",ylab="daily avg no of steps",main="weekend",col="blue")
plot(levels(mynewdata$interval), wdaysteps, type="l", xlab="interval",ylab="daily avg no of steps",main="weekday",col="blue")
```

![plot of chunk P4](instructions_fig/P4-1.png)
