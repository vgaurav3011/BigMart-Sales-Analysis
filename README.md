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
    
## Data Preparation and Exploration

### Item Outlet Sales

- There are many outliers, in the Item Outlet Sales whose median is 1794.331, and there are many items at much higher price than the upper quadrant. This does not indicate need for removal of points with unusual behaviour as they can be products with higher prices such as electronics. However, we cannot see any such items in the Item Type list and thus it is indicative of many seasonal increase in the prices with a few exceptions. Also, only item outlet sales seems to have outliers and no other columns.

- The costliest product is a low fat household type item at 13000 approximately bought from the Supermarket The minimalist product cost is a low fat household item itself bought from the grocery store and a soft drink also bought from the grocery store. Hence, we cannot really comment directly based on item type and fat content whether it is priced higher or lower!

- The Item Outlet Sales is a one-tailed skewed distribution, which is indicating that the prices are more dense towards the left and has positive skewness with 1.177 value.

- The Medium sized outlets demonstrate highest amount of sales among all different outlet sizes

- Supermarket Type 3 has highest amount of sales which proves that urban areas and large outlet sizes have greater sales than grocery stores, and hence we are correct in our assumption.

- Medium Sized stores that can possibly be Supermarket-2 delivered best sales in earlier times of 1985, as we proceed towards the recent eras, the shift towards small sized grocery stores is an unusual observation proving our hypothesis wrong in assuming that high sized supermarkets should have best sales whatsoever.

- Medium sized outlets of Supermarket Type-3 have best sales in any category.
- Low fat content items have been sold most in Supermarket Type-3


![alt-text](https://raw.githubusercontent.com/vgaurav3011/BigMart-Sales-Analysis/master/images/Item%20Outlet%20Sales/distplot.png)
![alt-text](https://raw.githubusercontent.com/vgaurav3011/BigMart-Sales-Analysis/master/images/Item%20Outlet%20Sales/Outlet_Type.png)

![alt-text](https://raw.githubusercontent.com/vgaurav3011/BigMart-Sales-Analysis/master/images/Item%20Outlet%20Sales/OutletSize.png)

![alt-text](https://raw.githubusercontent.com/vgaurav3011/BigMart-Sales-Analysis/master/images/Item%20Outlet%20Sales/Years.png)

### Item Fat Content

- The item fat content has two distinct categories Low Fat and Regular which needs to be mapped along with LF, reg and low fat categorical values.
- There are many visible outliers in the item fat content that can be handled or removed if needed.
- Non-Consumable items having the prefix NC in the Item Identifiers should not have any fat content at all.
- The low-fat content items have higher sales than the corresponding Regular Fat items, and both have almost equitable distribution.
- Medium and Small Sized Outlets have higher sales of Low Fat Items than the High sized supermarkets.

![alt-text](https://raw.githubusercontent.com/vgaurav3011/BigMart-Sales-Analysis/master/images/Item%20Fat%20Content/OutletSize.png)


### Item MRP

- The highest sold items based on different types are Starchy Foods closely followed by Seafood and Dairy Products.
- The Item MRP is spread over a wide range, where the lower priced items, are having higher outlet sales, that indicates that more common needs or daily essentials have larger sales justifying our hypothesis.
- Item MRP is highly correlated with the Item Outlet Sales, making it one of the significant variables.
- The Item MRP is constant around different outlets and is thus independent of any outlet bias in terms of price range of different products.
- Item Weight is equally distributed over different MRPs and cannot be the deciding factor in this case.
- Item Visibility has no direct relationship with MRP either.

![alt-text](https://raw.githubusercontent.com/vgaurav3011/BigMart-Sales-Analysis/master/images/Item%20MRP/MRP.png)
![alt-text](https://raw.githubusercontent.com/vgaurav3011/BigMart-Sales-Analysis/master/images/Item%20MRP/TypeOutlet.png)
![alt-text](https://raw.githubusercontent.com/vgaurav3011/BigMart-Sales-Analysis/master/images/Item%20MRP/ItemType.png)
![alt-text](https://raw.githubusercontent.com/vgaurav3011/BigMart-Sales-Analysis/master/images/Item%20MRP/OutletSales.png)


### Item Visibility

- Item Visibility is not related to MRP in any much way and is equitably distributed
- A higher visibility does not indicate a direct increase in the item sales
- The item visibility does not have much of an impact in sales of Supermarket Type-1 in all areas
- It shows that it matters in terms of sales for medium sized grocery stores
- It matters in the Grocery Stores since 1985, but largely does not affect the Supermarkets all that much.
- Fat Content does not relate well with its visibility

![alt-text](https://raw.githubusercontent.com/vgaurav3011/BigMart-Sales-Analysis/master/images/Item%20Type/OutletType.png)

### Item Type

- Snack Foods and Fruits and Vegetables tend to have higher sales in the Supermarkets
- Grocery Stores also have high sales of Snacks, Fruits and Vegetables as well as Frozen Foods
- Essential items or daily needs have higher visibility
- Item Weight has no significant impact on the Types of items.

![alt-text](https://raw.githubusercontent.com/vgaurav3011/BigMart-Sales-Analysis/master/images/Item%20Type/Visibility.png)


## Modelling and Evaluation

- We tried Random Forest Regressor, Gradient Boosting, XGBoost and Decision Tree Models for Regression, out of which the most optimal tuned model was the Random Forest, and the other ensemble models performed optimally too.
- The Evaluation metric used is the Root Mean Squared Error with a least value of 1153 which came in top 4% of the leaderboard highest being 1127 on the Analyticsvidhya Janatahack.

# Summary

- Low Fat Content items have higher sales in both Tier-1 and Tier-3 cities equally almost, indicating diet consciousness is not constrained to urban areas.
- Items with higher visibility does not translate to higher sales or lower MRPs, infact visibility is equitable distributed.
- Snack Foods and Fruits and Vegetables have highest item sales in any outlet irrespective of locations.
- The higher aged Medium sized outlets displayed better sales than others.
- Supermarket Type-1 has larger size and translates to better sales, does not mean that well performing grocery stores are inferior to it, since they perform well with smaller size too.
- Supermarket Type-3 has most optimal sales performance followed by grocery stores in rural areas as well.
