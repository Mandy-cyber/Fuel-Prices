Tycoon Talk: Fuel Price Prediction
======
The Task
------
Given a list of recent fuel prices in Jamaica, which may be found [here](https://www.petrojam.com/price/), I will be predicting which fuel a theoretical business Tycoon should purchase in the week of July 1st to 8th 2022. However, to save a bucket load of time (not really), I'll only be advising the Tycoon between Gasolene 90 and Auto Diesel - i.e which of the two he/she/they should buy.

Table of Contents
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
The pandas package in Python has a really quick and easy function to get the basic summary/description of a dataframe. Voila,
````Python
import pandas as pd

df = pd.read_csv ('regdata.csv')
print(df.describe())
````


<br>

Types of Moving Averages
------
I'll be using and comparing three different moving averages to find the one closest to the historical data - assuming this is a good representation of future fuel prices. The three types are:

| **Abbreviation** |           **Name**             | **Calculation**  |
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
| ![image](https://user-images.githubusercontent.com/67931161/177079644-16d72f96-61fe-4bc3-b92b-eb7a83d04d07.png) |  ![image](https://user-images.githubusercontent.com/67931161/177080202-19022e15-8943-42d9-926d-62b46fe97c41.png) | 

<br>

Weighted Moving Average
------
When using WMA, the same observations were made as with the SMA. This ```prompts me to recommend Gasolene 90 to the Tycoon```.

| DATA | GRAPH | 
|------| ------|
| ![image](https://user-images.githubusercontent.com/67931161/177081651-995186f6-aee6-4e20-8920-2daf4e2c1689.png) | ![image](https://user-images.githubusercontent.com/67931161/177082047-372b1fce-8c13-46c9-b59a-09aedbdce05b.png) | 

<br>

Exponential Moving Average
------
When using EMA, the same observations as above were made. This, again,  ```prompts me to recommend Gasolene 90 to the Tycoon```.

| DATA | GRAPH | 
|------| ------|
| ![image](https://user-images.githubusercontent.com/67931161/177084715-7bc8ec40-1470-4d2a-9bd7-5b1206ae16dd.png) | ![image](https://user-images.githubusercontent.com/67931161/177084876-887307b7-b5fe-45b8-b7c3-b8e77616e75f.png) | 

<br>

Choosing The Best Price
------
All three averages showed that, theoretically-speaking, the Tycoon would pay less money to buy Gasolene 90 than Auto Diesel. It is now time to choose which of the moving averages is the most accurate and can be considered my [final prediction](https://github.com/Mandy-cyber/Fuel-Prices/edit/main/README.md#final-prediction). Observations:
* The 

<br>

Final Prediction
------



