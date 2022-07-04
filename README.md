Tycoon Talk: Fuel Price Prediction
======

The Task
------
Given a list of recent fuel prices in Jamaica, which may be found [here](https://www.petrojam.com/price/), I will be predicting which fuel a theoretical business Tycoon should purchase in the week of July 1st to 8th 2022. However, to save a bucket load of time (not really), I'll only be advising the Tycoon between Gasolene 90 and Auto Diesel - i.e which of the two he/she/they should buy.

The Process
------
1. Write a description of each fuel type because what even is Auto Diesel...
2. Get a summary of the data
3. Use moving averages on both fuel types
4. Get the deviation and hence average deviation for each type
5. Visualize and compare the fuel prices
6. Give Tycoon my recommendation

Descriptions
------
![alt text](https://jamaicancartrader.com/wp-content/uploads/2019/01/gas.jpg "Types of Fuel")
Gasolene comes in different 'Octane' ratings. You've heard of e.g Gasolene 87 or Gasolene 90. The below snippet from the [US Energy Information Administration](https://www.eia.gov/energyexplained/gasoline/octane-in-depth.php) explains it well:
> Octane ratings are measures of fuel stability. These ratings are based on the pressure at which a fuel will spontaneously combust (auto-ignite) in a testing engine. The octane number is actually the simple average of two different octane rating methods—motor octane rating (MOR) and research octane rating (RON)—that differ primarily in the specifics of the operating conditions. The higher an octane number, the more stable the fuel.

Gasolene 90 is a mid-range octane fuel. Now, about Diesel think of it like this: Diesel is thicker than gasolene which means that you get more power and mileage per gallon with Diesel. Autodiesel is just diesel for cars, SUVs and regular trucks.

Data Summary
------

