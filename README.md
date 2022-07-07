TABLE OF TASKS
======
* [Tycoon Talk: Fuel Price Prediction](https://github.com/StarApple-Intern-AR/Fuel-Prices/edit/main/README.md#tycoon-talk-fuel-price-prediction)
* [Tycoon Talk: All About Errors](https://github.com/StarApple-Intern-AR/Fuel-Prices/edit/main/README.md#tycoon-talk-all-about-errors)
* [Tycoon Talk: Regression in Python]()

<br>

--------------
Tycoon Talk: Fuel Price Prediction
======
The Task
------
Given a list of recent fuel prices in Jamaica, which may be found [here](https://www.petrojam.com/price/), I will be predicting which fuel a theoretical business Tycoon should purchase in the week of July 1st to 8th 2022. However, to save a bucket load of time (not really), I'll only be advising the Tycoon between Gasolene 90 and Auto Diesel - i.e which of the two he/she/they should buy.

Table of Contents - Fuel Price Prediction
------
* [The Task](https://github.com/Mandy-cyber/Fuel-Prices/edit/main/README.md#the-task)
* [The Process](https://github.com/Mandy-cyber/Fuel-Prices/edit/main/README.md#the-process)
* [Descriptions](https://github.com/Mandy-cyber/Fuel-Prices/edit/main/README.md#descriptions)
* [Data Summary](https://github.com/Mandy-cyber/Fuel-Prices/edit/main/README.md#data-summary)
* [Types of Moving Averages](https://github.com/Mandy-cyber/Fuel-Prices/edit/main/README.md#types-of-moving-averages)
* [Choosing The Best Price](https://github.com/Mandy-cyber/Fuel-Prices/edit/main/README.md#choosing-the-best-price)
* [Final Prediction](https://github.com/Mandy-cyber/Fuel-Prices/edit/main/README.md#final-prediction)

<br>

The Process
------
1. Write a description of each fuel type because what even is Auto Diesel...
2. Get a summary of the data
3. Use moving averages on both fuel types
4. Get the deviation and hence average deviation for each type
5. Visualize and compare the fuel prices
6. Give Tycoon my recommendation

<br>

Descriptions
------
Gasolene comes in different 'Octane' ratings. You've heard of e.g Gasolene 87 or Gasolene 90. The below snippet from the [US Energy Information Administration](https://www.eia.gov/energyexplained/gasoline/octane-in-depth.php) explains it well:
> Octane ratings are measures of fuel stability. These ratings are based on the pressure at which a fuel will spontaneously combust (auto-ignite) in a testing engine. The octane number is actually the simple average of two different octane rating methods—motor octane rating (MOR) and research octane rating (RON)—that differ primarily in the specifics of the operating conditions. The higher an octane number, the more stable the fuel.

Gasolene 90 is a mid-range octane fuel. Now, about Diesel think of it like this: Diesel is thicker than gasolene which means that you get more power and mileage per gallon with Diesel. Autodiesel is just diesel for cars, SUVs and regular trucks.

<br>

Data Summary
------
The pandas package in Python has a really quick and easy function to get the basic summary/description of a dataframe, which can be seen below. Furthermore, looking at the description, I do not recognize any outliers or potential errors in the data.

````Python
import pandas as pd

df = pd.read_csv ('regdata.csv')
print(df.describe())
````

<img align="left" src="https://user-images.githubusercontent.com/67931161/177185818-4ed008ac-5a47-48c4-88d1-234c6590da24.gif" height="48%" width="48%">
<img align="right" src="https://user-images.githubusercontent.com/67931161/177186805-939af9cd-3f79-471f-830d-0b4a60ec6dea.png" height="48%" width="48%">
<br clear="left">

<br>
<br clear="left">

Types of Moving Averages
------
I'll be using and comparing three different moving averages to find the one closest to the historical data - assuming this is a good representation of future fuel prices. The three types are:

| **Abbreviation** |       **Name**         | **Calculation**  |
| :------------|:---------------------------| :----------- |
| **SMA**      | Simple Moving Average      | Sum of values divided by the number of values | 
| **WMA**      | Weighted Moving Average    | (price * weighting factor) + (Price of previous period * weighting factor-1) |
| **EMA**      | Exponential Moving Average | (closing price − previous day's EMA) ×k + previous day's EMA <br /> k is 2 ÷ (number of time periods + 1)|

<br>

Simple Moving Average
------
When using SMA, the average standard deviation of gasolene fuel prices is less than that of auto diesel which suggests the calculated gasolene values to be more accurate. That, paired with the predicted price (highlighted in red) of gasolene being lower than auto diesel, 
<br> ```prompts me to recommend Gasolene 90 to the Tycoon```.

| DATA | GRAPH | 
|------| ------|
| ![image](https://user-images.githubusercontent.com/67931161/177079644-16d72f96-61fe-4bc3-b92b-eb7a83d04d07.png) |  ![image](https://user-images.githubusercontent.com/67931161/177181516-a9ee0df9-c025-425f-bb9b-5827a15c34e2.png) | 

<br>

Weighted Moving Average
------
When using WMA, the same observations were made as with the SMA. This ```prompts me to recommend Gasolene 90 to the Tycoon```.

| DATA | GRAPH | 
|------| ------|
| ![image](https://user-images.githubusercontent.com/67931161/177081651-995186f6-aee6-4e20-8920-2daf4e2c1689.png) | ![image](https://user-images.githubusercontent.com/67931161/177181442-e72f79c1-5fbb-4eb7-b17c-7829421f1460.png) | 

<br>

Exponential Moving Average
------
When using EMA, the same observations as above were made. This, again,  ```prompts me to recommend Gasolene 90 to the Tycoon```.

| DATA | GRAPH | 
|------| ------|
| ![image](https://user-images.githubusercontent.com/67931161/177084715-7bc8ec40-1470-4d2a-9bd7-5b1206ae16dd.png) | ![image](https://user-images.githubusercontent.com/67931161/177181929-51f565a8-67d2-4ab1-a655-859cf40e9d19.png) | 

<br>

Choosing The Best Price
------
<img align="right" src="https://user-images.githubusercontent.com/67931161/177182055-c64de8c5-1365-479b-8a1b-6cb087cd206c.png" height="50%" width="50%">
<img align="right" src="https://user-images.githubusercontent.com/67931161/177206446-b7c03444-8427-4e90-951f-2db452fc459a.png" height="50%" width="50%">

All three averages showed that, theoretically-speaking, the Tycoon would pay less money to buy Gasolene 90 than Auto Diesel. It is now time to choose which of the moving averages is the most accurate and can be considered my [final prediction](https://github.com/Mandy-cyber/Fuel-Prices/edit/main/README.md#final-prediction). Observations:
* The price calculated using EMA had the smallest average standard deviation. This average deviation is calculated with a 4 week time period.
* Looking at the graph, throughout the Jan 2020 - June 2022 time period, the WMA and EMA calculations have been the closest to the actual price. Even during the Feb 2022 period where the fuel prices suddenly go off-trend (due to the start of the Ukraine-Russia war) the WMA and EMA calculations stay closest to reality. The EMA remains the closest.
* Really the competition is between EMA and WMA. In my opinion, the EMA value is the best choice due to how its calculated, and of course we can see its accuracy when looking at the standard deviation and the graph. Whilst both the EMA and WMA place more weight on recent values, the WMA's weights remain constant, whereas the EMA is inconsistent and hence more dynamic with its weightage as a result of it being exponential. Accordingly, the EMA calculations are able to react quicker to sudden price changes. 

```
Calculation for July 7th 2022 Fuel Price 
= 219.2698507 - (-3.171806891)
= 222.441657591
```

<br>

Final Prediction
======
All things considered, next week the Tycoon should purchase ```Gasolene 90``` and will pay approximately ```$222.44/gallon```.

<br>

Learning Resources
------
What I read to do this task:
* https://www.pythonfordatascience.org/descriptive-statistics-python/
* https://www.wallstreetmojo.com/moving-average-in-excel/
* https://www.eia.gov/energyexplained/gasoline/octane-in-depth.php
* https://www.google.com/search?q=what+is+auto+diesel&oq=what+is+auto+diesel&aqs=chrome..69i57j0i512j0i22i30j69i60l5.2539j0j4&sourceid=chrome&ie=UTF-8
* https://www.statology.org/exponential-moving-average-google-sheets/
* https://www.investopedia.com/ask/answers/122314/what-exponential-moving-average-ema-formula-and-how-ema-calculated.asp
* https://www.investopedia.com/articles/trading/10/simple-exponential-moving-averages-compare.asp

<br>

-----------
Tycoon Talk: All About Errors
======
The Task
------
Part two of the fuel price prediction task is to calculate the errors of our predictions. Previously, I only looked at the deviation and the average deviation, now I'll be looking at 5 other types of errors and will calculate them for my chosen fuel - Gasolene 90.

Table of Contents - All About Errors
------
* [Error Types](https://github.com/Mandy-cyber/Fuel-Prices/edit/main/README.md#error-types)
* [Mean Error](https://github.com/Mandy-cyber/Fuel-Prices/edit/main/README.md#mean-error)
* [Mean Absolute Error](https://github.com/Mandy-cyber/Fuel-Prices/edit/main/README.md#mean-absolute-error)
* [Mean Squared Error](https://github.com/Mandy-cyber/Fuel-Prices/edit/main/README.md#mean-squared-error)
* [Root Mean Square Error](https://github.com/Mandy-cyber/Fuel-Prices/edit/main/README.md#root-mean-square-error)
* [MAPE](https://github.com/Mandy-cyber/Fuel-Prices/edit/main/README.md#mape)
* [Errors for Full Time Period](https://github.com/Mandy-cyber/Fuel-Prices/edit/main/README.md#errors-for-full-time-period)

<br>

Error Types
------
There are several _several_ different types of errors that can be calculated and used for a variety of different use cases; however, for this task we'll be looking at the following types.
1. Mean Error
2. Mean Absolute Error
3. Mean Squared Error
4. Root Mean Square Error
5. Mean Absolute Percentage Error (MAPE)

<br>

**N.B - These errors are calculated on a monthly basis i.e the mean deviation shown in a row is the mean of the deviations for the past 4 weeks of fuel prices. Additionally, click on images to see them larger.**

Mean Error
------
| CALCULATION | RESULT | 
|-------------|--------|
| ![image](https://user-images.githubusercontent.com/108837959/177859782-1766ad10-26a3-4fc8-8f7a-7e0cfe64161f.png) | ![image](https://user-images.githubusercontent.com/108837959/177857752-4970edff-fb9d-4670-bedb-7ab1f8cc79af.png) |

<br>

Mean Absolute Error
-------
| CALCULATION | RESULT |
|-------------|--------|
| ![image](https://user-images.githubusercontent.com/108837959/177861057-09bbee98-8735-47fc-93c1-7ebd3694a602.png) | ![image](https://user-images.githubusercontent.com/108837959/177858267-8f709e1c-9041-4419-a88d-4d056bff7bb1.png) | 

<br>

Mean Squared Error
-------
| CALCULATION | RESULT |
|-------------|--------|
| ![image](https://user-images.githubusercontent.com/108837959/177860937-6c027ddd-c1f5-44b5-9399-9e39230f7d7b.png) | ![image](https://user-images.githubusercontent.com/108837959/177861023-c73bc689-ec6a-4fbd-81f7-f909931c830b.png) | 

<br>

Root Mean Square Error
-------
| CALCULATION | RESULT |
|-------------|--------|
| ![image](https://user-images.githubusercontent.com/108837959/177861289-837fdfd4-4ca7-4634-b01d-338725a3c04b.png) | ![image](https://user-images.githubusercontent.com/108837959/177861324-2d50fecc-e88f-48a8-8709-93d29e08918b.png) | 
 
<br>

MAPE
-------
| CALCULATION pt1 | CALCULATION pt2 | RESULT |
|-----------------|-----------------|--------|
| ![image](https://user-images.githubusercontent.com/108837959/177862313-375bb2ef-8622-4869-b1a4-aa7d4fbc01f0.png) | ![image](https://user-images.githubusercontent.com/108837959/177862767-b1880217-6645-4f91-8969-99826de612bf.png) | ![image](https://user-images.githubusercontent.com/108837959/177862809-3f4c8094-da38-47ed-a3c0-f1c270dc46cd.png) |

<br>

Errors for Full Time Period
------
The above errors were done per month, the below errors are for the entire dataset.
* **Mean Error** = **_JMD_** 1.377597761
* **Mean Absolute** Error = **_JMD_** 1.377597761
* **Mean Squared Error** = **_JMD^2_** 8.663948773
* **Root Mean Square Error** = **_JMD_** 2.943458641
* **MAPE** = 0.7672057212 **_%_**

---------------------------------------------

