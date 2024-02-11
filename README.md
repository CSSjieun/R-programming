# R-programming

## Chapter 1. Data Analysis and Data Cleaning
### 2.6 Feature Engineering
Creating new variable using variables from the present dataset.

### 3.1 Exploratory Data Analysis
Exploring the data normally using Max, Min, Median, Mean, and Mode.
We need to understand the implied phenomenon embedded in the data to resolve the problem correctly.

Check NA or outliers in single variable and if there are any NAs or outliers then clean it.
To check the data distribution, summarise the variable simply and see the data distribution using Box Plot or Stem-and-Leaf Plot.

More than two variables' relationship can be caputured by Scatter Plot.
Scatter Plot let us know how much the data spread, linear relationship, and cluster existence.

### 4. Data Analysis
1) Statistical Hypothesis
  Analysis method will be determined by hypothesis and variable types.

2) Machine Learning
   We compare the algorithm for prediction and classfication model and use the well performing algorithm.

3) Data Visualization
   
### 4.1. Statistical Hypothesis Testing
From the exploratory data analysis stage, we clarify the problem.
In the data analysis stage, we need to find the algorithm to resolve the clarified problems.

When we analyze the data we need to focus on "if the analysis result will bring us a profit."
We cannot get the information more than understading the phenomenon with obtained data such as customer's gender, age, and geographical infromation. 
We at least need to know which factor will make profit of our service, if it is possible to change the factor, and if net profit can be produced compared to cost.

### 4.2. Machine Learning
There are mainly three machine learning methods: supervised learning (Purpose of classification or numerical prediction), unsupervised learning (Purpose of subdividing a specific group through clustering), reinforcement learning (The purpose is to observe the environment and find optimized goals through rewards and penalties).

1) Supervised Learning
   Supervised learning is a method of providing answers and training, and is used for classification models and regression models.
   Mainly predict the uncoming event or issue using past data.

   It predict or estimate an output (response) from various inputs (predictors)
   Statistical tools: better understanding about the relationship between the response and the predictors (inference)
   Maching learning tools: better (prediction accuracy)
   --> Most widely used tools: regression, classification, text analytics, recommendation systems, time series

2) Unsupervised Learning
   Unsupervised learning is a method of training without answers, and is used to explore data to find properties similar to the structure and classify them.
   For example, we can classify customers to one cluster who has similar buying pattern of specific products and accomplish the goal to increase the profit providing promotion to     
   induce the repurchase of the product (Cluster Analysis or Association Rule).
   We can use Principal Component Analysis or Kernel PCA to reduce the dimensionality of the data.

   Tools for understanding data, with no target attribute (no labels). Usually organize into some natural groups.
   Difficult to know how well your are doing; useful as a pre-processing step for supervised learning.
   --> Most widely used tools: PCA, clustering/segmentation, association rules

3) Reinforcement Learning
   Training the agent to receive as many rewards as possible within a given environment by its action.
   For example, it is used to create AI players in the game industry or to develop autonomous driving in cars (ex. AlphaGo).

4) Others: semi-supervised learning, optimization, simulation, . . .

### 4.3. Visualization
Data visualization is the process of finding hidden patterns in the complex and disorderly flow of data and processing them concisely, clearly, and visually to convey them.

### 4.4. Making conclusion
The analysis report is the result of organizing business plans, policy proposals, and ideas into a report according to requirements.
In the introduction, the background of the analysis and the contents of the analysis are generally written.
Main contents include how the analysis was performed and what the analysis results were.
In the conclusion, a solution to the analysis topic using the analysis results is presented and the expected effects are written accordingly to increase justification.
Lastly, we conclude by presenting future projects(or plans) on what projects will be performed in the future.

## Chapter 2
### 5. What happened in the cafe for last 1 year.
### 5.1. readxl package
```R
 install.packages("readxl")
 library("readxl")
 read_xlsx()
```

 table(cafe$season)
 --> fall: 24354, winter:13977, spring:10436, summer:13643
 --> Relatively number of order in fall is high because data collection started from 2017.09(fall) to 2020.12(winter).
 *We should consider this fact when we present the result of analysis.

### Frequency of each item(beverage)
cafe_tr = data.frame(table(cafe$item))
### price & item
cafe_item = subset.data.frame(cafe, select=c("item", "price"))
### only one item and its price
cafe_item = unique(cafe_item)
### price of item, item, Frequ
item_list = merge(cafe_tr, cafe_item, by.x="Var1", by.y="item")
### Calculate the total saled price for each item
item_list$amount = item_list$Freq * item_list$price
sum(item_list$amount)

### Weekend sales
cafe$weekday = weekdays(cafe$order_date)
date_info = data.frame(weekday = c("Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"),
                      day = c("weekday", "weekday", "weekday", "weekday", "weekday", "weekend", "weekend"))
cafe = merge(cafe, date_info)
table(cafe$day)

### Sesonal sales
cafe$month = months(cafe$order_date)
for (i in 1:nrow(cafe)) {
  if (cafe$month[i] == "January") {
    cafe$season[i] = "winter"
  } else if(cafe$month[i] == "February") {
    cafe$season[i] = "winter"
  } 
  else if (cafe$month[i] == "March") {
  cafe$season[i] = "spring"
  } else if (cafe$month[i] == "April") {
  cafe$season[i] = "spring"
  } else if (cafe$month[i] == "May") {
  cafe$season[i] = "spring"
  }
  else if (cafe$month[i] == "June") {
    cafe$season[i] = "summer"
  } else if (cafe$month[i] == "July") {
    cafe$season[i] = "summer"
  } else if (cafe$month[i] == "August") {
    cafe$season[i] = "summer"
  }
  else if (cafe$month[i] == "September") {
    cafe$season[i] = "fall"
  } else if (cafe$month[i] == "November") {
    cafe$season[i] = "fall"
  } else if (cafe$month[i] == "December") {
    cafe$season[i] = "fall"
  }
  else
    cafe$season[i] = "winter"
}

or

for (i in 1:nrow(cafe)) {
  if(cafe$month[i] == "December"|cafe$month[i] == "January"|
     cafe$month[i] == "February") {
    cafe$season[i] = "winter"
  } else if(cafe$month[i] == "March"|cafe$month[i] == "April"|
            cafe$month[i] == "May") {
    cafe$season[i] = "spring"
  } else if(cafe$month[i] == "June"|cafe$month[i] == "July"|
            cafe$month[i] == "August") {
    cafe$season[i] = "summer"
  } else
    cafe$season[i] = "fall"
}

### 5.5 Visualization
geom_point() => point, scatter
geom_line() => line
geom_bar(stat="identity") => bar
geom_col => bar
geom_tile => tile bar
geom_raster() => grid
geom_text() => text expression
geom_area() => area 
geom_path() => order connection
geom_polygon() => polygon
geom_histogram() => histogram

### theme
theme_gray()
theme_bw()
theme_linedraw()
theme_light()
theme_dark()
theme_minimal()
theme_minimal()
theme_classic()
theme_void()

### format of date
cafe$date_ym = format(cafe$order_date, "%Y-%m")
%Y - ex) 1990,2021
%y - ex) 90, 21
%y - month(01 - 12) ex) 02, 03
%d - day(01 - 31) ex) 14, 22
%w - day of the week(0 - 6) 0:sunday ex) 1
%p - beforenoon/ afternoon ex) afternoon
%H - time (00 - 23) ex) 23
%I - time (00 - 12) ex) 11
%M - minute (00 - 59) ex) 43
%S - second (00 - 59) ex) 30

## Chapter 6. The effect of the advertisement
### Data description
city 1: municipal
city2: city
age: age
sex: sex
type: A/B test group separation
open: the number of email open
click: the number of opening the shoppingmall website
conversion: the number of purchase conversion
saels: total price of sales

### t-test
H0: There will be no mean difference of click between two groups
H1: There will be mean difference of click between two groups

### raster package
korea_sido = getData(name = "GADM", country = "kor", level = 1)
GID_1: code of sido
NAME_1: sido name in English 
VARNAME_1: sido name in various language
NL_NAME_1: sido name in Hanja
TYPE_1: type of sido
ENG_TYPE_1: sido type in Enlgish
HASC_1: short type of sido code

### Normality test
sample < 5000, shapiro.test()
sample => 5000, install.packages("nortest"), ad.test()

H0) Group A follows a normal distribution.
H1) Group A does not follow a normal distribution.

### Homoscedasticity test
normality yes - F-test
normality no - Levene test

install.packages("car")
leveneTest(y = adver$open, group = factor(adver$type))

H0) variation between groups are homogeneous
H1) variation between groups are heterogeneous

### conclusion
It was difficult to say that there was a statistical difference between the two groups in the number of times the email was opened because there was no exposure to the advertising content, but it was confirmed that there was a statistical difference starting from the area where the advertising was actually exposed. In particular, in the case of the number of clicks and purchase conversions, it can be said that advertisements delivered to B_GROUP showed more positive results than advertisements delivered to A_GROUP. In this way, the t-test plays an important role in evaluating the performance of two groups and making statistical decisions.

### fortify() function
In R, fortify() is a function primarily associated with the ggplot2 package, although it can be used in other contexts as well.
The purpose of fortify() is to convert data from a variety of formats into a data frame that can be used with ggplot2 for data visualization.

## Chapter 7. KOSPI (Korea Composite Stock Price Index) - time series data
Seasonal: St, Trend-cycle: Tt, Remainder: Rt
Addictive Model (when these three factors are independent each other): yt = St + Tt + Rt
Multiplicative Model (when three factors are dependent each other): yt = St * Tt * Rt

log Multiplicate Model --> Addictive Model format (easier to calculate)

log(yt) = logSt + logTt + log Rt

data from: Yahoo Finance
install.packages("quantmod")

### forecast package: time-series regression model
ts_data = ts(data = as.numeric(KOSPI_NEW$KS11.Close), frequency = 4)

library(forecast)
fit_lm = tslm(ts_data ~ trend)

pred = data.frame(forecast(fit_lm, h = 20), stringsAsFactors = FALSE)
pred |> ggplot(aes(x= index(pred), y = Point.Forecast)) +
  geom_line() +
  geom_ribbon(aes(ymin = Lo.95, ymax = Hi.95), alpha = 0.25) +
  geom_ribbon(aes(ymin = Lo.80, ymax = Hi.80), alpha = 0.5)

ts_data_B = ts(data = as.numeric(KOSPI_NEW$KS11.Close), frequency = 12)
fitted = tslm(ts_data_B ~ trend + season)

### Dummy variable t
t = time(ts_data_B)
t.break = data.frame(t, ts_data_B)
t.break[t.break$t < 3.65, ] = 0
t.break[t.break$t > 3.75, ] = 0
tb1 = ts(t.break$t, frequency = 20)

fit.t = tslm(ts_data_B ~ t)
AIC(fit.t)

### Utilizes quadratic functions to fit nonlinear trends.
fit.tb = tslm(ts_data_B ~ t + I(t^2) + I(t^3) + I(tb1^3))
AIC(fit.tb)

ts_data_B |> ggplot(aes(x = time(ts_data_B))) +
  geom_line(aes(y = ts_data)) +
  geom_line(aes(y = fit.t$fitted.values),
            color = "yellow", size = 1) +
  geom_line(aes(y = fit.tb$fitted.values), 
            color = "blue")


 
## References
Resource github: http://github.com/bjpublic/R_data
Advanced Modeling slides at UC3M Computation Social Science 2023/2024 academic year
The book:
• G. James, D. Witten, T. Hastie and R. Tibshirani.
An Introduction to Statistical Learning with Applications in R second edition available here: https://www.statlearning.com
Other references:
• K. Murphy
Machine Learning, A Probabilistic Perspective
• David Spiegelhalter
The Art of Statistics: Learning from Data
• C. Bishop
Pattern Recognition and Machine Learning








