# BigMart-Sales-Analysis

## Problem Statement

The data scientists at BigMart have collected 2013 sales data for 1559 products across 10 stores in different cities. Also, certain attributes of each product and store have been defined. The aim is to build a predictive model and find out the sales of each product at a particular store. Using this model, BigMart will try to understand the properties of products and stores which play a key role in increasing sales.

The problem will be addressed with the following procedures:

1. Hypothesis Generation
2. Exploratory Data Analysis
3. Feature Engineering
4. Model Building
5. Evaluation Metrics

## Data Understanding

We can identify the target variable to be the Item_Outlet_Sales, and rest of the features are inputs to the model and are independent variables of the dataset.

Based on each feature, we can describe them as follows:

Product based features:

    Item Identifier: Unique code for each item
    Item Weight: The weight of the item selected in data
    Item Fat Content: It is the amount of fats present in the item generally consumable edibles
    Item Visibility: The amount of how much an item is being sold as a range of 0-1
    Item Type: Dairy, Soft Drinks, Meat, Fruits and Vegetables and Household supplies

Outlet based features:

    Outlet Identifier: It is the unique code assigned to each outlet
    Outlet Establishment Year: The founding year of outlet
    Outlet Size: Bigger, Medium or Small
    Outlet Location: It is based on rural to urban in form of Tiers
    Outlet Type: Nature of the shop

Target Feature:

    Item Outlet Sales: Total sales done in the outlet
    

