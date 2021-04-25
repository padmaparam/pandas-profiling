# pandas-profiling

# Sale Price Prediction and Analysis of New York City Property
<br />[Introduction](#introduction)
<br />[Dataset](#dataset)
<br />[Analysis](#analysis)
<br />[Modelling](#modelling)
<br />[Future Research](#future-research)

<a name="introduction"></a>
## Introduction

This project is inspired by the new developments in the real estate despite the pandemic and wondering how the sales were in famous cities during the year 2020.   
<br /><br />The motive of this project is to see the trends in real estate in major boroughs of New York last year and predict the sale price for a residential or commercial unit. 


<a name="dataset"></a>
## Dataset

The data is extracted from New York department of Finance web site at this link. https://www1.nyc.gov/site/finance/taxes/property-rolling-sales-data.page
The data has properties that were sold during 2020 in New York city with a separate listing for each borough namely Manhattan, Bronx, Brooklyn, Queens, and Staten Island. All these listings were combined to a single list which helped compare the boroughs. The metrics that were part of this sales information were Borough, Neighborhood, Building Class Category, Tax class at present, Block, Lot, Easement, building class at present, Address, Apartment Number, ZIP code, Residential units, Commercial units, Total units, Land square feet, Gross square feet, Year built, Tax class at time of sale, Building class at time of sale, Sale price and Sale date. There were about 35000 observations.
<br /><br />The data includes for different tax classes. 
<br /><br />Class 1: Includes most residential property of up to three units (such as one-, two-, and three-family homes and small stores or offices with one or two attached apartments), vacant land that is zoned for residential use, and most condominiums that are not more than three stories. 
<br /><br />Class 2: Includes all other property that is primarily residential, such as cooperatives and condominiums. 
<br /><br />Class 3: Includes property with equipment owned by a gas, telephone, or electric company. 
<br /><br />Class 4: Includes all other properties not included in class 1,2, and 3, such as offices, factories, warehouses, garage buildings, etc.
<br /><br />Building Class Category: similar properties grouped by broad usage

<a name="analysis"></a>
## Analysis

The sale price was skewed, and some sales included 0’s where the property were transferred within the family or donated to charity. So only sales between 100,000 and 3 million were considered for analysis. Some sales included coops housing where people buy shares in that building and occupy. These were also considered as sales in our analysis and modelling. 
Here is the correlation matrix of main metrics used in the dataset. 
 
Residential Units and Total Units are highly correlated. Also, Commercial units and Land Square Feet is correlated. Hence removed Residential and Commercial Units in modelling.  Very few entries did not have year built which was removed.
Land Square Feet and Gross square Feet had many null values. These were filled using KNN imputing. Total Units that were not populated, were the coop housing. So, filled them with value 1. 
Here are some of the trends noticed in the real estate analysis. 
 
More sales were in Queens than other boroughs last year and Bronx had the least property sales
Some building categories had less than 10 sales, so they were merged to category Others. Here is the distribution of sale price for a given building category.

 

Factories had the highest sale price and condo hotels had the least median sale price.
Here is the distribution of vacant land purchases in 2020.
 
There are more chances of new housing and commercial construction in Staten Island than in other boroughs and the least in Manhattan. Same in terms of neighborhood.
 

 
Few houses in Brooklyn are incredibly old built in 1800's and their price is comparable with newer houses elsewhere. Bronx has comparatively lesser priced houses than other boroughs. Manhattan has more expensive houses.
 
More homes of higher tax brackets were sold in Queens and none in Manhattan in 2020. Also, very few commercial and industrial properties were sold last year probably due to COVID. Most of the sales for Manhattan was in Tax class 2 which is not surprising as it has many properties which has more than 3 units.
 
Residences that had 9 units had the highest median sale price compared to even higher units. The multi-unit building could be in Manhattan and the single unit could be in Brooklyn. Similarly, for commercial buildings below has 3 units as highly priced sales.

 


<a name="modelling"></a>
## Modelling

The categories Gender, Income, Card, Education and Marital status were all one hot encoded. The training data was standardized for some models.  We cannot afford to lose the customer here. If the customer is predicted that he will churn, but in real if he does not churn, it is bearable compared to other way. If we predict that the customer will not churn and if he churns, then we will lose a customer which is expensive. So, false negative is costly we are more concerned with recall. 
</br ><br />Tried different models to get better results. For a tree-based model, decided to choose Random Forest instead of Decision Tree as it has high variance and tendency to overfit. So, bias would be low. Hence considered multiple trees approach. Used Ensemble, Random Forest for bagging and Gradient Boosting for Boosting and got better results. 
Worked with different hyper parameters values before training each model. GridSearchCV is used for optimization of the hyper parameter. Performed a 5-fold cross validation. The best hyperparameter obtained during this process for each model is listed below.

<img src="https://github.com/padmaparam/Screenshots/blob/main/CustomerChurn/Picture17.png" style=" width:100px ; height:100px " />

Implemented the model using Scikit library. More details are available in the notebook for each model. The performance metrics collected are confusion matrix and classification report for each model. The best model was further verified by ROC curve and AOC value.
The highest accuracy for all models is 0.97 and the highest recall is 0.90. Over sampling helped improve the recall value by a small percentage. This table explains the outcomes of all models. 

<img src="https://github.com/padmaparam/Screenshots/blob/main/CustomerChurn/Picture18.png" style=" width:100px ; height:100px " />
Gradient Boosting is the best model looking at the recall value. It is even better after over sampling using SMOTE as the data set was imbalanced. 
The ROC curve explains the relation between True positive and True Negatives for our model.
<img src="https://github.com/padmaparam/Screenshots/blob/main/CustomerChurn/Picture19.png" style=" width:100px ; height:100px " /> 

The area under the ROC curve is 0.99246 
<a name="feature-importance"></a>
## Feature Importance
Important features were plotted for best model Gradient Boosting. 

<img src="https://github.com/padmaparam/Screenshots/blob/main/CustomerChurn/Picture20.png" style=" width:100px ; height:100px " /> 

Total transaction Count and Amount seems the most important feature for predicting the customer churn.
<a name="recommendation"></a>
## Recommendation
 	
The Bank can attract new male customers who earn between $40K and 80K annually by offering free trials as they tend to stay longer. Additional incentives can be given to them if they fall in the age range 45 to 55 and married. A new branch can be opened in the area where all the above criteria is met. These were observed when the data was explored.
<br /><br />But these factors contributed most to customer churn in order in our best model. Total Transaction Amount, Total Transaction Count, Total Revolving balance, Total Relationship Count, Total Count change between Q4 and Q1, Total Amount change between Q4 and Q1, Gender, Avg Utilization ratio, Credit Limit.
<a name="future-improvements"></a>
## Future Improvements

We can remove some more outliers and columns that are linear and investigate further. This can be combined with additional data of other products that the customers use in the same bank and cluster their behavior for further marketing. 
	



