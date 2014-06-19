---
title       : "Investigating the Fuel Economy Dataset 
Using k-Means Clustering in a Shiny App"
subtitle    : "Project for Coursera Developing Data Products"
author      : "Anne"
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

# About the Fuel Economy Data Sets

The http://fueleconomy.gov website, run by the U.S. Department of Energy's Office of Energy Efficiency and Renewable Energy and the U.S. Environmental Protection Agency, lists different estimates of fuel economy for passenger cars and trucks. For each vehicle, various characteristics are recorded such as the engine displacement or number of cylinders. Along with these values, laboratory measurements are made for the city and highway miles per gallon (MPG) of the car.

---
# A quick look at the head of the data set

```r
data(FuelEconomy)
head(cars2012)
```

```
##      EngDispl NumCyl Transmission    FE AirAspirationMethod NumGears
## 2199      4.7      8          AM7 28.79  NaturallyAspirated        7
## 2215      6.5     12           S7 22.62  NaturallyAspirated        7
## 2220      4.8     10           S6 21.96  NaturallyAspirated        6
## 2228      6.2      8          AM7 26.80  NaturallyAspirated        7
## 2229      1.6      4           S6 50.96  NaturallyAspirated        6
## 2230      1.6      4           M6 52.55  NaturallyAspirated        6
##      TransLockup TransCreeperGear          DriveDesc IntakeValvePerCyl
## 2199           0                0  TwoWheelDriveRear                 2
## 2215           1                0      AllWheelDrive                 2
## 2220           1                0  TwoWheelDriveRear                 2
## 2228           1                0  TwoWheelDriveRear                 2
## 2229           1                0 TwoWheelDriveFront                 2
## 2230           0                0 TwoWheelDriveFront                 2
##      ExhaustValvesPerCyl CarlineClassDesc VarValveTiming VarValveLift
## 2199                   2         2Seaters              1            0
## 2215                   2         2Seaters              1            0
## 2220                   2         2Seaters              1            0
## 2228                   2         2Seaters              1            0
## 2229                   2         2Seaters              1            1
## 2230                   2         2Seaters              1            1
```

---

Predictors extracted from the website include: EngDispl, NumCyl, Transmission, AirAspirationMethod, NumGears, TransLockup, TransCreeperGear, DriveDesc, IntakeValvePerCyl, ExhaustValvesPerCyl, CarlineClassDesc, VarValveTiming and VarValveLift. The outcome used in the book is in column FE and is the unadjusted highway data.

Data Set | Description
---------|--------------------------------
cars2010 | data in cars from model year 2010.
cars2011 | cars introduced in 2011 that were not in the model year 2010 data.
cars2012 |cars introduced in 2012 that were not in the model year 2010 or 2011 data

---

# k-Means Clustering

k-means clustering is a method of vector quantization, originally from signal processing, that is popular for cluster analysis in data mining. 

---
