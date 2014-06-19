---
title       : "Investigating the Fuel Economy Dataset 
Using k-Means Clustering in a Shiny App"
subtitle    : "Project for Coursera Developing Data Products"
author      : 
job         : 
framework   : html5slides        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

Investigating the Fuel Economy Dataset Using k-Means Clustering in a Shiny App

Project for Coursera Developing Data Products

---

Fuel Economy Data

Description

The http://fueleconomy.gov website, run by the U.S. Department of Energy's Office of Energy Efficiency and Renewable Energy and the U.S. Environmental Protection Agency, lists different estimates of fuel economy for passenger cars and trucks. For each vehicle, various characteristics are recorded such as the engine displacement or number of cylinders. Along with these values, laboratory measurements are made for the city and highway miles per gallon (MPG) of the car.

---


```r
data(FuelEconomy)
summary(cars2012)
```

```
##     EngDispl        NumCyl      Transmission       FE      
##  Min.   :1.30   Min.   : 4.0   M6     :19    Min.   :21.6  
##  1st Qu.:1.80   1st Qu.: 4.0   S6     :19    1st Qu.:31.8  
##  Median :2.50   Median : 5.0   A6     :12    Median :38.3  
##  Mean   :3.16   Mean   : 5.7   A5     :10    Mean   :39.7  
##  3rd Qu.:4.20   3rd Qu.: 7.0   A7     :10    3rd Qu.:49.0  
##  Max.   :6.50   Max.   :12.0   M5     : 5    Max.   :62.8  
##                                (Other):20                  
##          AirAspirationMethod    NumGears     TransLockup   
##  NaturallyAspirated:71       Min.   :1.00   Min.   :0.000  
##  Supercharged      : 4       1st Qu.:6.00   1st Qu.:0.000  
##  Turbocharged      :20       Median :6.00   Median :1.000  
##                              Mean   :5.87   Mean   :0.695  
##                              3rd Qu.:6.00   3rd Qu.:1.000  
##                              Max.   :8.00   Max.   :1.000  
##                                                            
##  TransCreeperGear                  DriveDesc  IntakeValvePerCyl
##  Min.   :0        AllWheelDrive         :13   Min.   :1.00     
##  1st Qu.:0        FourWheelDrive        :10   1st Qu.:2.00     
##  Median :0        ParttimeFourWheelDrive: 0   Median :2.00     
##  Mean   :0        TwoWheelDriveFront    :44   Mean   :1.93     
##  3rd Qu.:0        TwoWheelDriveRear     :28   3rd Qu.:2.00     
##  Max.   :0                                    Max.   :2.00     
##                                                                
##  ExhaustValvesPerCyl                    CarlineClassDesc VarValveTiming 
##  Min.   :1.00        2Seaters                   :16      Min.   :0.000  
##  1st Qu.:2.00        CompactCars                :15      1st Qu.:1.000  
##  Median :2.00        SubcompactCars             :12      Median :1.000  
##  Mean   :1.93        MinicompactCars            :11      Mean   :0.905  
##  3rd Qu.:2.00        MidsizeCars                :10      3rd Qu.:1.000  
##  Max.   :2.00        SpecialPurposeVehicleSUV4WD: 8      Max.   :1.000  
##                      (Other)                    :23                     
##   VarValveLift  
##  Min.   :0.000  
##  1st Qu.:0.000  
##  Median :0.000  
##  Mean   :0.316  
##  3rd Qu.:1.000  
##  Max.   :1.000  
## 
```

---

Predictors extracted from the website include: EngDispl, NumCyl, Transmission, AirAspirationMethod, NumGears, TransLockup, TransCreeperGear, DriveDesc, IntakeValvePerCyl, ExhaustValvesPerCyl, CarlineClassDesc, VarValveTiming and VarValveLift. The outcome used in the book is in column FE and is the unadjusted highway data.

cars2010  
data in cars from model year 2010.

cars2011	
cars introduced in 2011 that were not in the model year 2010 data.

cars2012	
cars introduced in 2012 that were not in the model year 2010 or 2011 data

---



