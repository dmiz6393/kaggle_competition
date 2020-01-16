# Project 2 - Ames Housing Data 



## Problem Statement

An investor has approached my construction company; she thinks there is an opportunity in Ames, Iowa to buy,refurnish and sell houses or buy land and build from scratch. He'd like to know what the biggest predictors are of higher valued houses, and if location matters. If there is an opportunity, she'd like to work with my construction company to begin the work together. 

Luckily, there is a data set that can help us answer these questions! The data dictionary used in this data analysis can be found here: http://jse.amstat.org/v19n3/decock/DataDocumentation.txt 

Our success can be validated if we are able to answer the following: 
1. Does location matter? 
2. What features correlated with higher selling houses? 
3. Where should we invest our time and money? 

## The Modeling Process and Executive Summary

We analyzed and cleaned the data, then built a model using the following process: 

1. Cleaning the data
    - We found that some ordinal and nominal values had NaN, instead of NA. We replaced this with either NA or None (indicated in the data dictionary). 
    - Other null values such as Lot Frontage or Garage Yr Built were replaced with mean values of those columns (there wasn't a sigificant difference between mean and median values). 
    - The rest of the null values were dropped, being that there were only 1 or 2 of them in each respective remaining category. 
    - We also made sure to lowercase and remove spaces from feature names. 
    - Some ordinal columns such as fireplace qu, garage_qual, exter_qual, and electrical columns were converted into numerical values to better assess their impact on saleprice 
2. EDA:
    - Initially we built a heatmap to see any strong correlations between saleprice and other columns. 
    - We also looked at if there were any significant differences between saleprice in various neighborhoods. 
    - Year sold didn't seem to make a significant difference in saleprice (surprisingly, given that one of these years was 2008 when the financial crisis occured)
    - We one hot encoded neighborhood and house style. 
3. Feature Engineering/ polynomial features 
    - We investigated whether or not there were stronger correlations with saleprice if we combined features such as garage cars, garage area, kitchen quality and kitchen number of kitchens. We did this for both train and test data and found there were stronger correlations when we put our features together! 

## Conclusions, Limitations, and Future Work

Initially, I used the linear regression model; this data (as much as it could) follows the MLR assumptions, and we are predicting a continuous outcome (saleprice) as well as impact of features on saleprice. In order to prevent our data from being overfit, I've also used Lasso and Ridge. There isn't a significant difference between the scores. We did not train-test-split here because we wanted to train our model with the data available to us. Potential downfalls of this model are that it could be too simplistic - there are many factors that go into the sale price of a house that this model might not take into account, such as the economy. We also risk not understanding what is truly important to the saleprice of the house.

It seems like there is potential for us to make a profit off of buying, renovating and selling houses in Ames Iowa. I believe the investor was right in coming to me and my team with this opportunity. 

The features that seemed to have the most impact on saleprice throughout the data are: 

- The square footage living area above ground and below ground (house style I believe fits in with this as well, since it contributes to the size of the house)
- The overall quality and condition 
- Garage area and cars 
- The year remod/add 
- The neighborhood

Negatively effected prices: 
- Low kitchen quality and basement quality

I believe we can be profitable if we focus our attention on: 

- Buying houses that are big/ have higher square footage in neighborhoods where houses are higher valued in general
- Renovate house so we can have a high rank in quality and condition 
- Ensure garage quality is up to par, and if house does not have a garage, build a garage that can fit at least two cars for it 
- Renovations alone on the house will increase the value! 

For further investigation, we would need to do some hypothesis testing. I am going to continue to feature engineer to see if we've missed any important features that, when put together, impact price. I'd also like to experiment with cleaning the data differently - perhaps using the mean scores for some rows wasn't the best approach. I would also add the above ground square footage and below ground square footage to get the total square footage and add this as a potential feautre in my model. We were limited in valuable information such as average age of house (investopedia predicted that this was an important factor in sales price). 